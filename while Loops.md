While loops – repeatedly repeat block of code as long as conidition is true 

Automate tasks 

Until becomes false 

 

While condition 

Do 

 

#code to be executed 

 

Done 

 

Count=1 

 

While [$count –le 5 ]  

Do 

Echo "count: $count" 

((count++)) (adds 1) 

Done 

 

Analyse data  

 

Fruits=("apple" "banana" "orange")  

 

Index=-0 (variable) 

 

While [ %index –lt ${#fruits[@] } 

Do 

Echo "fruit: ${fruit ${fruits[$index]}" 

((index++)) 

 

done 
