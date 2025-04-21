---
name: Database Design for University Game App
tools: [SQL / MySQL, RDBMS, UML Modeling]
image: assets/pngs/411-cover.png
description: Database application programming project which uses SQL for creating a Wordle-like UIUC game
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---
## Database Systems Project: UIUC Class of The Day Game

<p style="font-size: 16px; margin: 0;">
  <em>
  Fall 2024 Final project for <a href="https://alawini.web.illinois.edu/teaching/database-systems/">CS 411</a> at UIUC
  </em>
</p>
<p style="font-size: 14px; margin-top: 0;">Group Members: James Mallek, Kavya Moharana, Sruthi Kode, Samidha Sampat</p>

---

<p style="font-size: 14px; margin: 0;">Languages, Libraries, and Tools Used</p>
>
<a href="https://dev.mysql.com/doc/" target="_blank" rel="noreferrer"> <img src="https://static-00.iconduck.com/assets.00/database-mysql-icon-1849x2048-81vgyimd.png" alt="MySQL" width="50" height="50"/>
<a href="https://www.uml.org/" target="_blank" rel="noreferrer"> <img src="https://www.fortux.com/img/uml_logo.svg" alt="uml" width="65" height="65"/>
<a href="https://www.uml.org/" target="_blank" rel="noreferrer"> <img src="https://static-00.iconduck.com/assets.00/google-cloud-icon-2048x1646-7admxejz.png" alt="gcp" width="55" height="55"/>

#### Project Summary and Application Description

Each day, a random UIUC class will be selected as the ‘Class of the Day’. Users will be able to guess different courses from the university until they get it right. After each incorrect guess, the app will reveal which parts of the guess were right or wrong, such as department or course number. Once the user has successfully guessed the course, a summary of the class will be displayed so that users can learn more about the wide variety of offerings on campus. Users who create an account will be able to see statistics on their guesses, like their average number of guesses or most guessed class. Account holders might also be able to save their favorite courses or track their guessing streaks to encourage long-term engagement.

Our application aims to foster community and bring students together through competition and conversation, as they try to guess the class of the day with the fewest amount of guesses. The Wordle-like daily challenge will promote both educational learning and social interaction on campus. While there are many social-media-esque apps catered towards college campuses (YikYak, ZeeMee, etc) we have not come across any such games or entertainment apps.

#### The Data
##### 1. UIUC Course Catalog Data from [Data Science Discovery](https://discovery.cs.illinois.edu/dataset/course-catalog/)
>
via Professor [Wade](https://waf.cs.illinois.edu/) Fagen-Ulmschneider, contains information on classes offered such as:
- **`Year [int]`**
- **`Term [object]`**
- **`Subject [object]`**
- **`Course Number [int]`**
- **`Course Description [object]`**
- **`Credit Hours [object]`**
- **`Degree Attributes [object]`**

##### 2. UIUC Class GPA Data from [Data Science Discovery](https://discovery.cs.illinois.edu/dataset/gpa/)
>
via Professor [Wade](https://waf.cs.illinois.edu/) Fagen-Ulmschneider, contains information on students' average GPA for classes offered such as:
- **`Course Title [object]`**
- **`Primary Instructor [object]`**
- **`Number of Students [int]`**
- individual variables for each possible **letter grade**

#### Entities and UML Diagram
![image tooltip here](assets/pngs/411-uml.png)

#### Database Implementation
```sql
CREATE TABLE Departments(
  DepartmentId VARCHAR(10),
  Name VARCHAR(255),
  PRIMARY KEY(DepartmentId)
);

CREATE TABLE Courses(
  CourseId Int,
  DepartmentId VARCHAR(10),
  Number Int,
  Name VARCHAR(255),
  Credits VARCHAR(50),
  GenEd VARCHAR(63),
  FOREIGN KEY(DepartmentId) REFERENCES Departments(DepartmentId),
  PRIMARY KEY(CourseId)
);

CREATE TABLE CourseDescription(
  CourseId Int,
  Description VARCHAR(1023),
  Instructors VARCHAR(255),
  FOREIGN KEY(CourseId) REFERENCES Courses(CourseId),
  PRIMARY KEY(CourseId)
);

CREATE TABLE User(
  UserId VARCHAR(31),
  Email VARCHAR(63),
  EncryptedPassword VARCHAR(255),
  DateJoined DATE,
  MostGuessed Int,
  AvgGuesses Decimal,
  FOREIGN KEY(MostGuessed) REFERENCES Courses(CourseId),
  PRIMARY KEY(UserId)
);

CREATE TABLE DailyClass(
  CurrentDate DATE,
  CorrectCourseId Int,
  MostCommonWrong Int,
  TotalAvgGuesses Decimal,
  FOREIGN KEY(CorrectCourseId) REFERENCES Courses(CourseId),
  PRIMARY KEY(CurrentDate)
);

CREATE TABLE Guess(
  GuessId Int,
  UserId VARCHAR(31),
  CurrentDate DATE,
  CourseId INT,
  FOREIGN KEY(UserId) REFERENCES User(UserId),
  FOREIGN KEY(CurrentDate) REFERENCES DailyClass(CurrentDate),
  FOREIGN KEY(CourseId) REFERENCES Courses(CourseId),
  PRIMARY KEY(GuessID)
);
```

##### Queries
```sql
SELECT Departments.DepartmentId, COUNT(GuessId) AS TimesGuessed
FROM Departments 
JOIN Courses ON Departments.DepartmentId = Courses.DepartmentId
JOIN Guess ON Guess.CourseId = Courses.CourseId
WHERE Guess.CurrentDate = '2024-08-21'
GROUP BY Departments.DepartmentId
ORDER BY TimesGuessed DESC;
```

```sql
SELECT User.UserId, User.Email, Courses.Name AS CorrectCourseName
FROM Guess
	JOIN DailyClass ON Guess.CurrentDate = DailyClass.CurrentDate
	JOIN Courses ON DailyClass.CorrectCourseId = Courses.CourseId
	JOIN User ON Guess.UserId = User.UserId
WHERE Guess.CourseId = DailyClass.CorrectCourseId 
AND Guess.CurrentDate = "2023-11-14";
```

```sql
SELECT Courses.CourseId, Courses.Name AS Course, Departments.Name AS Department, COUNT(Guess.GuessId) AS FrequentGuess
FROM Courses 
JOIN Guess ON Courses.CourseId = Guess.CourseId
JOIN Departments ON Courses.DepartmentId = Departments.DepartmentId
GROUP BY Courses.CourseId, Courses.Name
ORDER BY FrequentGuess DESC
LIMIT 15;
```