Or hashbang 

#!/bin/bash 

 

Always first line 

 

Serves as directive for how the system interprets the file 

 

Sh also runs 

Bash also runs 

 

the shebang line starts with the hash followed by an exclamation mark.  

 

It specifies the interpreter or shell that should handle the script.  

 

It enables consistent execution of scripts across different environments regardless of whatever shell you're using. Even though we're using the zsh shell here, it was still able to interpret the greet.sh file as a bash script.  

 

You can specify different interpreters for different types of scripts and the shebang line should be placed as the first line of the scripts without any leading spaces or characters before it. 

 
