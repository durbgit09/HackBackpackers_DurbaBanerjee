# HackBackpackers_DurbaBanerjee

Problem Statements

Problem Statement 1 - Lineage problem statement

1) Creating stored procedure
2) Passing the sql statement as provided in the problem statement 
3) And executing it with SQL override query

  CREATE PROCEDURE col_tab_value 
AS
  SELECT  distinct COLUMN_NAME,TABLE_NAME from  
(sql_statement)  (# given problem_statement) 
  WHERE TABLE_NAME like ('%_T' or '%_S')
 and COLUMN_NAME like ('T.%' or 'S.%') 
GO;

  EXEC col_tab_value
  
  
  NOTE- We can extract the column names with this query as well - SELECT *
FROM INFORMATION_SCHEMA.COLUMNS
WHERE TABLE_NAME = N'TABLE_NAME'



Problem Statement 2 - Functions problem statement

Replacing the datastage functions with equivalent ADF functions

As I am not expert in python/javascript, please consider it as a psuedo code 

Solution:

  1. def time_func():
   x=currentTimestamp()
   return x
   
   
2. def date_func():
   x=int(input())
   y= toLong( currentTimestamp() - toTimestamp('1970-01-01 00:00:00.000', 'yyyy-MM-dd HH:mm:ss.SSS') ) * 1000|   (#ex: converting to unix)
   z=y-x
   t=toUTC(z)
   return t
   
   
3. def part_func():
   x=datetime(2022-10-30 01:02:03)
   y = datetime_part("minute", x)
   return y
   
4. def time_unix():
   x= toLong( currentTimestamp() - toTimestamp('1970-01-01 00:00:00.000', 'yyyy-MM-dd HH:mm:ss.SSS') ) * 1000|
   return x
   
   
5. def binary_func():
   x=int(input())
   y=int(input())
   z=binary_and(x,y)
   return z
   
6. def binary_func2():
   x=int(input())
   y=int(input())
   z=binary_or(x,y)  (# add the binary value to give decimal output)
   return z
   
7. def abs_value():
  x=int(input())
  abs_val=abs(x)
  return abs_val

8. def floor_value():
  x=float(input()) (#ex-5.56)
  floor_val= bin(x,1)  (#bin() is alias of floor())
  return floor_val

9. def random_num():
   x=rand(1000)
   return x
   

10. def null_func():
   isnotnull([value])
   
   
11. def null_val():
   val=input()
   iff(
   isnull("val") == true
     val='hi')
   else (val='null')
   return()
   
12. def double_val():
   x=int(input())
   y= todouble(x)
   return y

13. def split_val():
   x=float(input())  (# ex: 243.7890)
   y=string(x)
   z=split(y,".",2)
   return int(z)
   
14. def len_func():
   x=str_len()
   return x
   
15. def alph_num():
   x=input() 
   y= input() (# ex: AB99, AB100)
   iif(
   x has ((("A" -"Z") || ("a" -"z") ) && ('0' -'9'))
     return (1)
   )
  return(0)
   
   
   
16. def rep_str():
   x=input() 
   lookup_val=input()
   rewrite_val=input()
   y= replace_string(x, lookup_val, rewrite_val)
   return y
  

17. def num_shift():
   input1=int(input())
   input2=int(input())
   iif(greater(input1, input2), '1','-1')
   return()
   
   
18. def split_val():
   x=input() (#ex: 'ab','abc','abcd')
   index_num=int(input())
   z=split(x,",",index_num)
   return z
   
19. def rep_str():
   x=input() (#ex: abc)
   count=int(input())
   y=strrep(x, count)
   return y



Problem Statement 3 - XML problem statement


1)Description:Expression for setting up date format:

Source(exp_cntry_multi_def_cd)--> transformation(Expression) -->IN_OUTPUT_RUNDATE???EXPRESSION="TO_DATE&#xD;&#xA;(IN_OUTPUT_RUNDATE ,&apos;YYYY-MM-DD&apos;)-->target(OUT_DW_AS_OF_DT)

-->IN_AUDIT_UPDT_TS???EXPRESSION= TO_DATE(IN_AUDIT_UPDT_TS,&apos;YYYY-MM-DD HH24.MI.SS&apos;)-->Target(OUT_AUDIT_UPDT_TS)

