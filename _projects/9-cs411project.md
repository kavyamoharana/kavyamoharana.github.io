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
  Fall 2024 Final Project for <a href="https://alawini.web.illinois.edu/teaching/database-systems/">CS 411</a> at UIUC
  </em>
</p>
<p style="font-size: 14px; margin-top: 0;">Group Members: James Mallek, Kavya Moharana, Sruthi Kode, Samidha Sampat</p>

---

<p style="font-size: 14px; margin: 0;">Languages, Libraries, and Tools Used</p>
>
<a href="https://dev.mysql.com/doc/" target="_blank" rel="noreferrer"> <img src="https://static-00.iconduck.com/assets.00/database-mysql-icon-1849x2048-81vgyimd.png" alt="MySQL" width="50" height="50"/>
<a href="https://www.uml.org/" target="_blank" rel="noreferrer"> <img src="https://www.fortux.com/img/uml_logo.svg" alt="uml" width="65" height="65"/>
<a href="https://www.uml.org/" target="_blank" rel="noreferrer"> <img src="https://static-00.iconduck.com/assets.00/google-cloud-icon-2048x1646-7admxejz.png" alt="gcp" width="55" height="55"/>

{% include elements/button.html link="https://github.com/kavyamoharana/kavyamoharana.github.io/blob/main/assets/pdfs/411-ProjectReport.pdf" text="View Full Report" size="sm" %}
{% include elements/button.html link="https://github.com/cs411-alawini/fa24-cs411-team116-KSS.git" text="Project GitHub Repository" size="sm" %}

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

<br>

#### Entities and UML Diagram

![image tooltip here](/assets/pngs/411-uml.png)

#### Database Implementation
Original connection/instance on GCP console:
<div style="display: flex; justify-content: center; gap: 5px;">
  <img src="/assets/jpegs/gcp-2.jpg" alt="gcp-1" width="500"/>
  <img src="/assets/jpegs/gcp-1.jpg" alt="gcp-1" width="500"/>
</div>

##### DDL commands
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
1. Finding the most commonly guessed departments on a given day
```sql
SELECT Departments.DepartmentId, COUNT(GuessId) AS TimesGuessed
FROM Departments 
JOIN Courses ON Departments.DepartmentId = Courses.DepartmentId
JOIN Guess ON Guess.CourseId = Courses.CourseId
WHERE Guess.CurrentDate = '2024-08-21'
GROUP BY Departments.DepartmentId
ORDER BY TimesGuessed DESC;
```
Output:
```sql
+--------------+---------------+
| DepartmentId | TimesGuessed |
+--------------+---------------+
| MCB          | 6             |
| HK           | 2             |
| ANTH         | 2             |
| EPSY         | 1             |
| GRK          | 1             |
| NPRE         | 1             |
| MUS          | 1             |
| CHEM         | 1             |
| ME           | 1             |
| ENGL         | 1             |
| MATH         | 1             |
| PHYS         | 1             |
| CPSC         | 1             |
| BADM         | 1             |
| LAT          | 1             |
| LAS          | 1             |
| ACE          | 1             |
| SOC          | 1             |
+--------------+---------------+
18 rows in set (0.03 sec)
```

2. Finding the users who guessed correctly on a given date
```sql
SELECT User.UserId, User.Email, Courses.Name AS CorrectCourseName
FROM Guess
	JOIN DailyClass ON Guess.CurrentDate = DailyClass.CurrentDate
	JOIN Courses ON DailyClass.CorrectCourseId = Courses.CourseId
	JOIN User ON Guess.UserId = User.UserId
WHERE Guess.CourseId = DailyClass.CorrectCourseId 
AND Guess.CurrentDate = "2023-11-14";
```
Output:
```sql
+-----------+-----------------------------+------------------------------+
| UserId    | Email                       | CorrectCourseName            |
+-----------+-----------------------------+------------------------------+
| michele56 | nicolecarr@example.net      | Advanced Modern Hebrew I     |
| djones    | martincarr@example.com      | Advanced Modern Hebrew I     |
| brooksbeth| mgonzalez@example.com       | Advanced Modern Hebrew I     |
| swalsh    | michaeljimenez@example.com  | Advanced Modern Hebrew I     |
| mallory86 | kmurphy@example.org         | Advanced Modern Hebrew I     |
+-----------+-----------------------------+------------------------------+
5 rows in set (0.01 sec)
```

3. Top 15 most frequently guessed courses overall
```sql
SELECT Courses.CourseId, Courses.Name AS Course, Departments.Name AS Department, COUNT(Guess.GuessId) AS FrequentGuess
FROM Courses 
JOIN Guess ON Courses.CourseId = Guess.CourseId
JOIN Departments ON Courses.DepartmentId = Departments.DepartmentId
GROUP BY Courses.CourseId, Courses.Name
ORDER BY FrequentGuess DESC
LIMIT 15;
```
Output:
```
+---------+-------------------------------------------------------------+-----------------------------------------------+----------------+
| CourseId| Course                                                      | Department                                    | FrequentGuess  |
+---------+-------------------------------------------------------------+-----------------------------------------------+----------------+
| 78066   | Organizational Communication and Community Impact           | Communication                                 | 31             |
| 29891   | Ruminant Nutrition                                          | Animal Sciences                               | 26             |
| 75881   | Psychology of Prejudice and Discrimination                  | Psychology                                    | 24             |
| 66151   | Graphic Design Inquiry                                      | Art and Design                                | 20             |
| 77550   | Economic Development and Migration                          | Economics                                     | 20             |
| 29951   | Senior Design Project Lab                                   | Electrical and Computer Engineering           | 19             |
| 62996   | Video Reporting & Storytelling                              | Journalism                                    | 19             |
| 73742   | Point of Care Ultrasound                                    | Clinical Sciences and Engineering             | 19             |
| 54570   | Tax Research                                                | Accountancy                                   | 19             |
| 69955   | Professional SBC Capstone Project                           | Strategic Brand Communication                 | 19             |
| 30163   | Senior Thesis and Honors                                    | Comparative and World Literature              | 19             |
| 78358   | Multidisciplinary Innovation Studio                         | Human-Centered Design and Design Thinking     | 18             |
| 58770   | Advanced Topics in Science and Technology Journalism        | Journalism                                    | 18             |
| 55433   | DGS Study Abroad                                            | General Studies                               | 18             |
| 65088   | BFA Thesis Production                                       | Dance                                         | 18             |
+---------+-------------------------------------------------------------+-----------------------------------------------+----------------+
15 rows in set (0.04 sec)
```

##### Indexing Analysis

```sql
/* Example for Query 1 */

EXPLAIN ANALYZE SELECT Departments.DepartmentId, COUNT(GuessId) AS TimesGuessed
FROM Departments
JOIN Courses ON Departments.DepartmentId = Courses.DepartmentId
JOIN Guess ON Guess.CourseId = Courses.CourseId
WHERE Guess.CurrentDate = '2024-08-21'
GROUP BY Departments.DepartmentId
ORDER BY TimesGuessed DESC;

CREATE INDEX Course_Id ON Guess(CourseId);
CREATE INDEX Dept_Id ON Courses(DepartmentId);
CREATE INDEX Current_Date ON Guess(CurrentDate);
```
We did not notice a difference in our results or cost when indexing for the four queries. There are likely several reasons why the change in indexing did not bring a better effect on our queries’ performances. Most likely, the indexing was redundant due to MySQL’s automatic indexing. Our dataset also might have low-selectivity where scanning or filtering would be faster than accessing the index. This means variables like CurrentDate may have had many repeated values, leading to limited performance gains. Additionally, more complex queries such as these (with nested joins) can render indexing to be ineffective. Overall, for an index to improve query performance it should match the query structure and be used on high-selectivity columns. Creating queries that use different attributes could avoid the automatic indexing issue, however this would not improve overall performance.

#### Advanced Database Programs
Our application contains a **trigger** that updates a user’s favorite course (most guessed class) as it changes. The most guessed course can be seen by users in their information page which also displays other interesting user details and is where users can decide to change their email or delete their account. Without the trigger, we would have to recalculate the most guessed class every time it was checked. 

The application also has a **stored procedure** which is called for every guess. It takes a department, number, user ID, and the current date to create a new record in the guess table as well as return information about the course guessed and the correct class. This allows the backend to wrap this information in a JSON format for the frontend to display to users. The user sees the department, number, name, number of credits, and Gen Ed of the guessed course. They also see whether they were right, wrong, too high, or too low for these attributes. This means they will be more informed for their next guess.

Advanced database programs such as the trigger complement our application by improving performance and scalability by minimizing computation. The stored procedure also improves consistency and efficiency within the database logic. 

