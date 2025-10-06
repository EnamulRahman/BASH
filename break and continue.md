Additional control  

 

Interrupt loop 

 

Break statement; exists loop  

 

Within loop you'll have if statement, then broken if rule met 

 

If want to continue then continue instead of break 

 

$ while true 

> do 

> echo "count: $count" 

> ((count++)) 

> if [ $count -eq 4 ] 

> then 

> break 

> fi 

> 

> done 

 

// 
