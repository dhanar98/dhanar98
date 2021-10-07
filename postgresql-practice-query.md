### CREATE A TABLE

```sql
CREATE TABLE COMPANY(
   ID INT PRIMARY KEY     NOT NULL,
   NAME           TEXT    NOT NULL,
   AGE            INT     NOT NULL,
   ADDRESS        CHAR(50),
   SALARY         REAL,
   JOIN_DATE	  DATE
);
```

### DROP A TABLE

```sql
DROP TABLE COMPANY
```

### CREATE SCHEMA

```sql
create schema myschema;

create table myschema.company(
   ID   INT              NOT NULL,
   NAME VARCHAR (20)     NOT NULL,
   AGE  INT              NOT NULL,
   ADDRESS  CHAR (25),
   SALARY   DECIMAL (18, 2),
   PRIMARY KEY (ID)
);
```

### DROP SCHEMA

```sql
DROP SCHEMA myschema; - > EMPTY SCHEMA

DROP SCHEMA myschema CASCADE; - > ALL CONSTARINTS REMOVED
```

### INSERT QUERY

> SYNTAX:
```sql
INSERT INTO TABLE_NAME VALUES (value1,value2,value3,...valueN);
```

> QUERY :
```sql
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY,JOIN_DATE) VALUES (1, 'Paul', 32, 'California', 20000.00,'2001-07-13');
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,JOIN_DATE) VALUES (2, 'Allen', 25, 'Texas', '2007-12-13');
INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY,JOIN_DATE) VALUES (3, 'Teddy', 23, 'Norway', 20000.00, DEFAULT );

MUltiple INSERT VALUES IN SAME QUERY

INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY,JOIN_DATE) VALUES (4, 'Mark', 25, 'Rich-Mond ', 65000.00, '2007-12-13' ), (5, 'David', 27, 'Texas', 85000.00, '2007-12-13');

```

### SELECT QUERY

> SYNTAX:
```sql
SELECT column1, column2, columnN FROM table_name;
```

> QUERY:

**DISPLAY ALL THE DETAILS IN THE TABLE**
```sql
SELECT * FROM COMPANY;
```

**DISPLAY PARTICULAR COLUMN DETAILS IN TABLE**

```sql
SELECT NAME,AGE,ADDRESS FROM COMPANY

```

### ARITHMETIC OPERATIONS

> QUERY

```sql
select 5+5 as sum ,5-5 as subtract ,5*5 as multiply,5/5 as division ,5%5 as remainder;
```

### LOGICAL OPERATORS

> QUERY
```sql
SELECT 1|1 AS _OR,1&1 AS _AND, ~1 AS _NOT
```

### WHERE CLAUSE

> SYNTAX

```sql
SELECT column1, column2, columnN
FROM table_name
WHERE [search_condition]

```

> QUERY

```sql
SELECT * FROM COMPANY WHERE AGE >= 25 AND SALARY >= 65000;
```

### AND,OR CLAUSE

> SYNTAX - AND:

```sql
SELECT column1, column2, columnN
FROM table_name
WHERE [condition1] AND [condition2];
```

> QUERY
```sql
SELECT * FROM COMPANY WHERE AGE >= 25 AND SALARY >= 65000;
```
> SYNTAX - OR:

```sql
SELECT column1, columnN
FROM table_name
WHERE [condition1] OR [condition2];
```

> QUERY
```sql
SELECT * FROM COMPANY WHERE AGE >= 25 OR SALARY >= 65000;
```



