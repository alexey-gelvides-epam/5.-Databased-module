# Databased module

## Task 1

Please, complete the following task.

1. Design database for CDP program. Your DB should store information about students (name, surname, date of birth, phone numbers, primary skill, created_datetime, updated_datetime etc.), subjects (subject name, tutor, etc.) and exam results (student, subject, mark).
2. Please add appropriate constraints (primary keys, foreign keys, indexes, etc.).
3. Design such kind of database for PostrgeSQL. Show your design in some suitable way (PDF, PNG, etc). (1 point)
4. Try different kind of indexes (B-tree, Hash, GIN, GIST) for your fields. Analyze performance for each of the indexes (use ANALYZE and EXPLAIN). Check the size of the index. Try to set index before inserting test data and after. What was the time? Add your investigations to separate document. Test data: (1 point) 
    - 100K of users
    -  1K of subjects
    -  1 million of marks

    Test queries:
    -  Find user by name (exact match)
    -  Find user by surname (partial match)
    -  Find user by phone number (partial match)
    -  Find user with marks by user surname (partial match)

5. Add trigger that will update column updated_datetime to current date in case of updating any of student. (0.3 point)
6. Add validation on DB level that will check username on special characters (reject student name with next characters '@', '#', '$'). (0.3 point)
7. Create snapshot that will contain next data: student name, student surname, subject name, mark (snapshot means that in case of changing some data in source table – your snapshot should not change). (0.3 point)
8. Create function that will return average mark for input user. (0.3 point)
9. Create function that will return avarage mark for input subject name. (0.3 point).
10. Create function that will return student at "red zone" (red zone means at least 2 marks <=3). (0.3 point)
11. Extra point (1 point). Show in tests (java application) transaction isolation phenomena. Describe what kind of phenomena is it and how did you achieve it.
12. Extra point 2 (1 point). Implement immutable data trigger. Create new table student_address. Add several rows with test data and do not give acces to update any information inside it. Hint: you can create trigger that will reject any update operation for target table, but save new row with updated (merged with original) data into separate table.

## Other rules:

- Please, add your changes to GIT task by task. It will be better to check your result based on such kind of history;
- Database table/constraint creation – separate file;
- Test data for indexes – separate file.

### The result of your task is:

- DB design in suitable format;
- Index investigation document;
- SQL file that will show to your mentor and tutor how you did your homework.

## Task 2 

Within the database designed in the previous task write the following queries:

1. Select all primary skills that contain more than one word (please note that both ‘-‘ and ‘ ’ could be used as a separator). – 0.2 points
2. Select all students who do not have a second name (it is absent or consists of only one letter/letter with a dot). – 0.2 points
3. Select number of students passed exams for each subject and order result by a number of student descending. – 0.2 points
4. Select the number of students with the same exam marks for each subject. – 0.2 points
5. Select students who passed at least two exams for different subjects. – 0.3 points
6. Select students who passed at least two exams for the same subject. – 0.3 points
7. Select all subjects which exams passed only students with the same primary skills. – 0.3 points
8. Select all subjects which exams passed only students with the different primary skills. It means that all students passed the exam for the one subject must have different primary skill. – 0.4 points
9. Select students who do not pass any exam using each of the following operator: – 0.5 points
    - Outer join
    - Subquery with ‘not in’ clause
    - Subquery with ‘any ‘ clause Check which approach is faster for 1000, 10K, 100K exams and 10, 1K, 100K students
10. Select all students whose average mark is bigger than the overall average mark. – 0.3 points
11. Select the top 5 students who passed their last exam better than average students. – 0.3 points
12. Select the biggest mark for each student and add text description for the mark (use COALESCE and WHEN operators) – 0.3 points
    - In case if the student has not passed any exam ‘not passed' should be returned.
    - If the student mark is 1,2,3 – it should be returned as ‘BAD’
    - If the student mark is 4,5,6 – it should be returned as ‘AVERAGE’
    - If the student mark is 7,8 – it should be returned as ‘GOOD’
    - If the student mark is 9,10 – it should be returned as ‘EXCELLENT’
13. Select the number of all marks for each mark type (‘BAD’, ‘AVERAGE’,…). – 0.4 points 

### The result of your task is

- SQL file that will show to your mentor and tutor how you did your homework.
- Query optimization investigation is provided as a separate document. 

# Lectures: 

- Database design: Overall - https://learn.epam.com/detailsPage?id=eb5a27e9-c682-4922-b4a0-7366169f913d          
- Scalable design for high load - https://learn.epam.com/detailsPage?id=44a6c487-bcf9-4108-a808-6c1afc88ce3b
- Basic SQL: SQL basics with Oracle RDBMS - https://learn.epam.com/detailsPage?id=56dad214-9215-40f3-9199-6dddad57c04d
- Advanced SQL for Query Tuning and Performance Optimization - https://learn.epam.com/detailsPage?id=cf3d74d6-e934-4398-a971-334f29fd728b
- [NoSQL (Mongo, Cassandra):]  
    - part 1 - https://learn.epam.com/detailsPage?id=20a1397a-9cfe-4e4c-9237-7a7a368b3940         
    - part 2 - https://learn.epam.com/detailsPage?id=53e64be1-5838-4613-a3d4-cbcdd8bea167
- [Neo4J] 
    - intro - https://www.youtube.com/watch?v=U8ZGVx1NmQg
    - cypher - https://www.youtube.com/watch?v=1TSBXZMv6tc
- Advanced SQL for Query Tuning and Performance Optimization - https://learn.epam.com/detailsPage?id=cf3d74d6-e934-4398-a971-334f29fd728b
- SQL operators - https://learn.epam.com/detailsPage?id=38df8b06-acf4-4758-b70c-719d238c0b2c
- Advanced SQL: Logical Query Processing, Part 1 - https://learn.epam.com/detailsPage?id=ea8c0ff2-6cc8-467e-bc63-31f94509edf5
- Advanced SQL: Logical Query Processing, Part 2  (Optional) - https://learn.epam.com/detailsPage?id=223b9d4a-836b-4c62-ac18-2f2a6cb7a439
- Advanced SQL for Data Scientists - https://learn.epam.com/detailsPage?id=badf3272-e4b2-4c8c-9a2a-93b98883bd32

# Books

- PostgreSQL: Up and Running (Regina O. Obe, Leo S. Hsu)
- MongoDB in Action (Kyle Banker)
- Learning Neo4j (Rik Van Bruggen)
- PostgreSQL: Up and Running (Regina O. Obe, Leo S. Hsu)

# Sites

- PostgreSQL tutorial - https://www.postgresql.org/docs/9.6/static/tutorial.html
- Tutorialspoint postgreSQL - https://www.tutorialspoint.com/postgresql/
- MongoDB tutorial - https://docs.mongodb.com/manual/tutorial/
- Tutorialspoint mongoDB - https://www.tutorialspoint.com/mongodb/
- Tutorialspoint Cassandra - https://www.tutorialspoint.com/cassandra/
- Neo4j get-started - https://neo4j.com/developer/get-started/
- Neo4j CypherQL - https://neo4j.com/developer/cypher-query-language/

# Additional links to a conference presentation or popular education videos: 

- Initial materials on KB - https://kb.epam.com/display/GDOKB/CDP+JaMP+-+Kharkiv+fall+2017#CDPJaMP-Kharkivfall2017-Databases
