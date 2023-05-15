# INTEGRITY CONSTRAINTS
## Q1) Create the table Department with the attributes listed.

```sql
CREATE TABLE DEPT (
  DEPT_NO NUMBER(5) PRIMARY KEY,
  DNAME VARCHAR(10),
  DLOC VARCHAR(10)
);
```

## Q2) Create table EMP with columns listed below. Add PRIMARY KEY constraint for EMPNO column with constraint name. Give default constraint for Manager name.

```sql
CREATE TABLE EMP (
  EMP_NO NUMBER(5) CONSTRAINT PK_EMP PRIMARY KEY,
  ENAME VARCHAR(10),
  JOB VARCHAR(10),
  MANAGER_NAME VARCHAR(10) DEFAULT 'Mr.K. RAM',
  HIRE_DATE DATE,
  SALARY NUMBER(30),
  COMMISSION NUMBER(30),
  DEPT_NO NUMBER(5)
);
```

# Q3) Add Unique key constraint to the column DNAME of DEPT table

```sql
ALTER TABLE DEPT ADD CONSTRAINT UQ_DNAME UNIQUE (DNAME);
```

## Q4) Add ‘NOT NULL’ constraint to the column ‘hire date’ in the dept table.

```sql
ALTER TABLE EMP MODIFY HIRE_DATE DATE NOT NULL;
```

## Q5) Add Check constraint to the table EMP to restrict the values of salary lies between 10,000 and 20,000.

```sql
ALTER TABLE EMP ADD CONSTRAINT CHK_SALARY_RANGE CHECK (SALARY BETWEEN 10000 AND 20000);
```

## Q6) Add Foreign key constraint to the column DEPTNO of EMP table references DEPTNO of DEPT table.

```sql
ALTER TABLE EMP ADD CONSTRAINT FK_DEPTNO_DEPT FOREIGN KEY (DEPT_NO) REFERENCES DEPT(DEPT_NO);
```

## Q7) Add Check constraint to the table EMP to restrict the values of commission. It has to be less than 10%.

```sql
ALTER TABLE EMP ADD CONSTRAINT CHK_COMMISSION CHECK (COMMISSION < 0.1 * SALARY);
```

## Q8)Do insertion in the above two tables as per the rules given below.

1. Insert data into the table which satisfies the constraints on DEPT table first.

```sql
INSERT INTO DEPT (DEPT_NO, DNAME, DLOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');
```

2. Insert data into the table which satisfies the constraints on EMP table and keep the default
value for manager.

```sql
INSERT INTO EMP (EMP_NO, ENAME, JOB, HIRE_DATE, SALARY, COMMISSION, DEPT_NO) VALUES (7369, 'SMITH', 'CLERK', '17-DEC-80', 11800, NULL, 10);
```

## Q9) Insert data in to the EMP table not satisfying the foreign key constraints. Notice the error and mention it .

```sql
INSERT INTO EMP (EMP_NO, ENAME, JOB, HIRE_DATE, SALARY, COMMISSION, DEPT_NO) VALUES (7499, 'ALLEN', 'SALESMAN', '20-FEB-81', 11600, NULL, 30);
```
# OUTPUT
```
Error: FOREIGN KEY constraint failed
```

## Q10) Remove the primary key constraint on the EMP table.

```sql
ALTER TABLE EMP DROP CONSTRAINT PK_EMP;
```
