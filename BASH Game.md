LEVEL 1:  

 

cd, mkdir, touch  

 

Level 2:  

 

Save file as .sh first 

 

#!/bin/bash 

 
 
for i in {1..10} 
 

 

do 
    echo $i 
 

 

done 

 

Explanation: 

for i in {1..10}: Starts a loop that iterates from 1 to 10. 

echo will display the current number (i) in each iteration. 

 

 

Level 3:  Write a script that checks if a file named hero.txt exists in the Arena directory. If it does, print Hero found!; otherwise, print Hero missing!. 

 

USE –f to see if a file is present 

 

Use square brackets in the conditional if statement 

 

chmod 

 

#!/bin/bash  

if [ -f "Arena/hero.txt" ]; then 
 

    echo "Hero found!" 
 

else 
    echo "Hero missing!" 
 

 

fi 

 

REMEMBER:  

 

Forgetting spaces around [ and ] (e.g. if [ -f"foo" ] will fail). 

 

Not quoting the path (use "Arena/hero.txt"). 

 

Running script from another directory — relative paths are relative to the current working directory. If you want the path relative to the script file itself, that requires a small extra line (I can show that if you want). 

 

 

Level4:  

 

 Create a script that copies all .txt files from the Arena directory to a new directory called Backup 

 

 

Cd .. 

 

#!/bin/bash 
 
 

 

mkdir -p Backup 
 

 

cp Arena/*.txt Backup/ 

 

Level 5: 

 

1. Creates a directory names 'Battlefield' 
2. Inside Battlefield, create files named knight.txt, sorcerer.txt, and rogue.txt. 
3. Check if knight.txt exists; if it does, move it to a new directory called Archive. 
4. List the contents of both Battlefield and Archive. 

 

ATTEMPT:  

 

 

mkdir battlefield 

touch knight.txt > battlefield 

touch sorcerer.txt > battlefield 

touch rogue.txt > battlefield 

  

if [ -f knight.txt ]; then 

        mv knight.txt > mkdir archive 

fi 

  

ls battlefield 

ls archive 

 

 

These are the error codes:  

 

./level5.sh: line 5: battlefield: Is a directory 

./level5.sh: line 6: battlefield: Is a directory 

./level5.sh: line 7: battlefield: Is a directory 

ls: cannot access 'archive': No such file or directory 

 

 

Fix:  

 

> is used to output text into a file 

 

Cant mkdir like that  

 

#!/bin/bash 

  

# 1. Create Battlefield directory 

mkdir -p Battlefield 

  

# 2. Create files inside Battlefield 

touch Battlefield/knight.txt 

touch Battlefield/sorcerer.txt 

touch Battlefield/rogue.txt 

  

# 3. Check if knight.txt exists, move it to Archive 

if [ -f Battlefield/knight.txt ]; then 

    mkdir -p Archive 

    mv Battlefield/knight.txt Archive/ 

fi 

  

# 4. List contents of both directories 

echo "Contents of Battlefield:" 

ls Battlefield 

  

echo "Contents of Archive:" 

ls Archive 

 

 

Level 6:  

 

Write a script that accepts a filename as an argument and prints the number of lines in that file. If no filename is provided, display a message saying 'No file provided' 

 

Level 6: 

Argument Parsing 

Mission: Write a script that accepts a filename as an argument and prints the number of lines in that file. If no filename is provided, display a message saying 'No file provided'. 

 

-z = test operator if string is empty 

 

$1 is user input 

 

if [ -z "$1" ]; then 

    echo "No file provided" 

else 

Use wc –l to count lines in a file  

 

If you just do wc -l "$1", it prints both the number and the filename. 

wc -l < "$1" 

lines=$(wc -l < "$1") 

 Store it in a variable 

 

echo "Number of lines: $lines" 

// 

 

 

if [ -z "$1" ]; then 

    echo "No file provided" 

else 

    lines=$(wc -l < "$1") 

    echo "Number of lines: $lines" 

fi 

 

 

Level 7: File Sorting Script 

 

Write a script that sorts all .txt files in a directory by their size, from smallest to largest, and displays the sorted list. 

 

// ls *.txt 

 

* is a wildcard for any characters. 

 

stat -c "%s %n" file.txt 

 

Stat command gives meta data about files 

 

Here: 

%s → size in bytes 

%n → file name 

 

 

Sorting is done by the sort command 

 

// sort –n  

 

Have to pipe the information from one command to another 

 

-c means custom 

  

// stat –c "%s %n" level7text.txt | sort –n 

 

DIRECTORY="Arena"  

 

if [ ! -d "$DIRECTORY" ]; then  

 

echo "Directory does not exist."  

exit 1  

fi  

find "$DIRECTORY" -type f -name "*.txt" -exec ls -lh {} + | sort -k 5,5 -h | awk '{ print $5, $9 }' 

 

 

Level 8: 

 

 Create a script that searches for a specific word or phrase across all .log files in a directory and outputs the names of the files that contain the word or phrase. 

 

// grep tool for searching 

 

//  grep "error" system.log 

 

specific word or phrase. 

Output only the file names that contain it. 

 

 

There’s a flag for that: -l (lowercase L) → “list files with matches.” 

 

grep -l "error" *.log 

 

Search for all wor 

 

only want file names. 

There’s a flag for that: -l (lowercase L) → “list files with matches.” 

 

 

grep -l "disk failure" *.log 

 

DIRECTORY=$1 

SEARCH_TERM=$2 

  

# check if directory exists 

if [ ! -d "$DIRECTORY" ]; then 

    echo "Directory does not exist." 

    exit 1 

fi 

  

grep -rl "$SEARCH_TERM" "$DIRECTORY" 

 

grep -l "$SEARCH_TERM" "$DIRECTORY"/*.log searches for the term in each .log file and lists the filenames that contain the term. 

 

 

Level 9: Script to Monitor Directory Changes 

Mission: Write a script that monitors a directory for any changes (file creation, modification, or deletion) and logs the changes with a timestamp. 

 

if [ ! -d "$DIRECTORY" ] → The -d flag checks if the path is a directory. 

! negates it, so it’s checking “if it does NOT exist”. 

 

DIRECTORY="Arena" 

LOG_FILE="change_log.txt"  

 

if [ ! -d "$DIRECTORY" ]; then  

echo "Directory does not exist."  

exit 1  

fi  

fswatch -r "$DIRECTORY" | while read event; do if [ -e "$event" ]; then echo "$(date +'%Y-%m-%d %H:%M:%S') File modified/created: $event" >> "$LOG_FILE" else echo "$(date +'%Y-%m-%d %H:%M:%S') File deleted: $event" >> "$LOG_FILE" fi done 

 

fswatch -r "$DIRECTORY" watches the directory recursively for changes. 

 

fswatch -r "$DIRECTORY" watches the directory recursively for changes. 
