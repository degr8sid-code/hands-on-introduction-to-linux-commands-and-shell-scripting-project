# Linux Commands and Shell Scripting - Final Project
*Estimated time needed: 90 minutes*

## Introduction
Congratulations!! You have finished the modules. Now is the time to put your skills to test. Read through the scenario below.

This lab may use some bash concepts we haven't yet covered in this course. Whenever this happens, we will provide sufficient hints and/or the code for you.

## Scenario
You are a **lead linux developer** at the top-tech company "ABC International INC." ABC currently suffers from a huge bottleneck - each day, interns must painstakingly access encrypted password files on core servers, and backup those that were updated within the last 24-hours. This introduces human error, lowers security, and takes an unreasonable amount of work.

As ABC INC's most trusted linux developer, you have been tasked with creating a script **backup.sh** which automatically backs up any of these files that have been updated within the past 24 hours.

## Objectives
The objective of this lab is to incorporate much of the shell scripting you've learned over this course into a single script. You will schedule your shell script to run every 24 hours using crontab.

*TIP: If you're unsure whether some of your code will work as wanted, you can try the command directly in the terminal - and even create your own test scripts!*

## Task List

### Task 1
Navigate to # [TASK 1] in the code.

Set two variables equal to the values of the first and second command line arguments, as follows:

Set targetDirectory to the first command line argument
Set destinationDirectory to the second command line argument
(This task is meant to help with code readability)

### Task 2
Display the values of the two command line arguments in the terminal.

### Task 3
Define a variable called currentTS as the current timestamp, expressed in seconds.

### Task 4
Define a variable called backupFileName to store the name of the archived and compressed backup file that the script will create.
The variable backupFileName should have the value "backup-[$currentTS].tar.gz".

For example, if currentTS has the value 1634571345, then backupFileName should have the value backup-1634571345.tar.gz.

### Task 5
Define a variable called origAbsPath with the absolute path of the current directory as the variable’s value.

### Task 6
Define a variable called destAbsPath with value equal to the absolute path of the destination directory.

### Task 7
Change directories from the current working directory to the target directory targetDirectory.

### Task 8
Task 8
You need to find files that have been updated within the past 24 hours.
This means you need to find all files who’s last modified date was 24 hours ago or less.

To do make this easier: Define a numerical variable called yesterdayTS as the timestamp (in seconds) 24 hours prior to the current timestamp, currentTS.

### Task 9
Within the $() expression inside the for loop, write a command that will return all files and directories in the current folder.

### Task 10
Inside the for loop, you want to check whether the $file was modified within the last 24 hours.
To get the last-modified date of a file in seconds, use date -r $file +%s
Then compare the value to yesterdayTS

Idea: if [[ $file_last_modified_date > $yesterdayTS ]] then the file was updated within the last 24 hours!
Since much of this wasn’t covered in the course, for this task you may copy the code below and paste it into the double round brackets (()):

`date -r $file +%s` > $yesterdayTS

### Task 11
In the if-then statement, add the $file that was updated in the past 24-hours to the toBackup array.
Since much of this wasn’t covered in the course, you may copy the code below and place after the then statement for this task:

toBackup+=($file)

### Task 12
After the for loop, compress and archive the files, using the $toBackup array of filenames, to a file with the name backupFileName.

### Task 13
Now the file $backupFileName is created in the current working directory. Move the file backupFileName to the destination directory located at destAbsPath.
