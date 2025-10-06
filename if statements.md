#!/bin/bash 

 

If condition 

Then 

… 

Fi 

 

Eq = equals 

Ne = not equal to 

Lt = less than 

Gt = greater than 

Le = less than or equal to 

Ge = greater than or equal to 

 

Square brackets 

 

If [ ] 

 

Age=25 

 

If [ $age –gt 18] 

Then 

Echo "you are an adult" 

Fi 

 

&& = and  

 

,|| or 

 

Grade=95 

 

If [ "$grade" –ge 90] && [$grade –le 100] 

 

Echo "well done" 

 

Fi 

 

== equal 

!= not equal 

 

Name=ahmed 


If 

["$name" == "ahmed" ] 

Then 

Echo "hello ahmed" 

Fi 

 

If statements allow you to make decisions and execute different code blocks based on conditions. 
Conditions are formed using comparison operators and logical operators. 
You can compare numbers, strings and combine conditions using logical operators and else clauses. 





