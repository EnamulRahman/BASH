 

Input values in parameters 

 

Pass parameters after script name 

 

./script.sh parameter1 parameter2 

 

Snippet display value of parameters 

 

#!/bin/bash 

  

echo "Parameter 1: $1" 

echo "Parameter 2: $2" 

echo "Parameter 3: $3" 

 

To echo all parameters we use  

 

echo "All Parameters: $@" 

 

Parameters are provided after a script name when executing a script. 

 

 Inside the script, parameters can be accessed using $1, $2, $3, and so on based on their position. The special variable $@ can be used to access all the parameters passed to the script.  

 

By allowing inputs through parameters, you can make your script more interactive and versatile. 
