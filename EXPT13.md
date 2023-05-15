# PL/SQL Cursors

# 1. Write a PL/SQL Block, to update salaries of all the employees who work in deptno 20 by 15%. If none of the employee’s salary are updated display a message 'None of the salaries were updated'. Otherwise display the total number of employee who got salary updated.
```
Declare
  num number(5);
Begin
  update emp set sal = sal + sal*0.15 where deptno=20;
  if SQL%NOTFOUND then
    dbms_output.put_line('none of the salaries were updated');
  elsif SQL%FOUND then
    num := SQL%ROWCOUNT;
    dbms_output.put_line('salaries for' || num || 'employees are updated');
  end if;
End;
```

# 2. Create a table emp_grade with columns empno &amp; grade. Write PL/SQL block to insert values into the table emp_grade by processing emp table with the following constraints.
If sal &lt;= 1400 then grade is ’C’
Else if sal between 1401 and 2000 then the grade is ‘B’ Else the grade is ‘A’.

```create table emp_grade(empno number, grade char(1));
Declare 
  Emp_rec emp%rowtype;
  Cursor c is select * into emp_rec from emp;
Begin
  Open c;
  If c%ISOPEN then
    Loop
      Fetch c into emp_rec;
      If c%notfound then Exit; Endif;
      If emp_rec.sal &lt;= 1400 then
        Insert into emp_grade values(emp_rec.empno,’C’);
      Elsif emp_rec.sal between 1401 and 2000 then
        Insert into emp_garde values(em_rec.empno,’B’);
      Else
        Insert into emp_garde values(em_rec.empno,’A’);
      Endif
    End loop;
  Else
    Open c;
  Endif;
End;
```
