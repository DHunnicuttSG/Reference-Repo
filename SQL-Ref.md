## SQL - Structured Query Language

### DML - Data Manipulation Language

Inserting Data:
Syntax: Insert into Table (field list) Values (Value list);
```
    insert into Contact(fName, lName) Values ("Jane", "Smith");
```

Updating Data:
Syntax: Update Table set field = ?? where (condition);
- When updating a database be sure to use conditions(i.e. contact ids) so you do not update the entire table
```
    update Contact set fName = "Samantha" where id = 15;
```

Deleting Data:
Syntax: Delete from Table where (condition);
- Be sure to use conditions when deleting for same reason as updates
```
    delete from contact where id = 15;
```

Temporarily remove safe_updates to update or delete multiple rows of data
```
    Set SQL_SAFE_UPDATES = 0; -- Disable 
    Set SQL_SAFE_UPDATES = 1; -- Enable
```
***When you disable be sure to enable afterward***

Simple Query:
Syntax:
    SELECT [column names]
    FROM [Table Name]
    WHERE [Condition]

```
    SELECT id, fName, lName
    FROM student
    WHERE enrollmentDate > 10/10/2024;
```

Join Example Query:
Syntax:
    SELECT Table1.column1, Table1.column2, Table2.Column1 
    FROM table1
    [Join type] JOIN table2 ON [Relationship condition]
    WHERE [Filter Condition];

```
    SELECT s.fName, s.lName, c.courseName 
    FROM students as s
    Inner JOIN course ON s.studentId = c.studentId
    WHERE courseId = 123;
```

### DDL - Data Definition Language

Delete a database:
Syntax: drop database if exists DB_NAME;
```
    drop database if exists SchoolDB;
```

Create and Use the current Database:
Syntax: create database if not exists DB_NAME; use DB_NAME;
```
    create database if not exists SchoolDB; 
    use SchoolDB;
```

Create a table:
Syntax: 
    Create table TBL_NAME (
        PKID int primary key auto_increment,
        CHAR_FIELD char(4) Not Null,
        BOOLEAN_FIELD boolean default false
    );
```
    create table band(
        bandId int primary key auto_increment,
        bandName varchar(50)
    );

    create table song(
        songId int primary key auto_increment,
        songTitle varchar(100),
        videoUrl varchar(255),
        bandId int,
        foreign key (bandId) references band(bandId)
    );
```

Create a relationship between tables:
Syntax: Foreign key (FKName) references tableName(PKName)
```
    -- from table above
       foreign key (bandId) references band(bandId)
```
*** colum names must be the same DATA TYPE ***


Change an existing column to hold more characters
```
    Alter table book  
	    Modify bookTitle varchar(200) not null;
```
Change a column name in a table:
```
    ALTER TABLE Publisher 
    RENAME COLUMN pub_name TO publisher_name
```

Remove colum from a table:
```
    Alter table Book
        Drop numPages;
```