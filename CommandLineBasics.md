# Command Line Basics
Here are the useful **BASH** commands that I learned,
```bash
whoami	#prints username
```
```bash
pwd	#prints current directory
```
```bash
cd <path>	#Navigate to path
```
```bash
ls <path>	#list files and folders in path
ls -F <path>	#specifies file/folder type
```
```bash
cd / 	#root directory
#Directory names in a path are separated with / on Unix, but \ on Windows
cd . 	#current directory
cd .. 	#directory above the current one
```
```bash
cp <old> <new>	#copies a file
```
```bash
rm <path>	#deletes a file
```
```bash
rm -r <path>	#deletes a folder -r stands for recurring
```
```bash
mv <source> <dest>	#move/rename a file
```
```bash
mkdir <path>	#creates new directory
```
```bash
touch <filename>	#creates new file
```
```bash
wc <filename>	#wordcount - shows lines, words, cahracters
wc -l	#-l lines, -w words, -m characters
```
```bash
ls <filename>	#confirms that file exists
```
```bash
cat <filename>	#displays whats in the file
```
---
### Wildcards
```bash
*.txt	#matches all files ending with .txt
p*.txt	#all files starting with p and ending with .txt, eg. python.txt, procrastination.txt, etc.
?ane.txt	#? to identify unknows character, eg. mane.txt, cane.txt, etc. But not chane.txt
m???ane.txt	#eg. methane.txt, but not minane.txt

#EXAMPLES
ls *t*ane.pdb	#shows all files whose names contain zero or more characters (*) followed by the letter t, then zero or more characters (*) followed by ane.pdb. This gives ethane.pdb methane.pdb octane.pdb pentane.pdb.
ls *t?ne.*	#shows all files whose names start with zero or more characters (*) followed by the letter t, then a single character (?), then ne. followed by zero or more characters (*). This will give us octane.pdb and pentane.pdb but doesn’t match anything which ends in thane.pdb.
ls *t??ne.pdb	#fixes the problems of option 2 by matching two characters (??) between t and ne. This is the solution.
ls ethane.*		#only shows files starting with 'ethane.'
```
---
### Storing Output
```bash
wc -l *.pdf > lengths.txt	#stores linecount of all files containing .pdf into lengths.txt
```
```bash
echo hello > test.txt	#overwrites test.txt and writes hello
echo hello >> test.txt	#appends 'hello' to the file
```
---
### Filtering Output
```bash
sort lengths.txt	#alphanumerically (ASCII) sorts in ascending order
sort -n lengths.txt	#numerically sorts and displays in ascending order
```
```bash
head lenghts.txt	#displays first 10 lines
head -n 6 lengths.txt	#displays first 6 lines of lengths.txt 
tail lenghts.txt	#displays last 10 lines
tail -n 6 lengths.txt	#displays last 6 lines of lengths.txt 
```
---
### Pipes
```bash
#use two commands together
wc -l *.pdb | sort -n	# send the output of wc directly to sort
wc -l *.pdb | sort -n | head -n 1	#send the output of wc directly to sort, and then send the resulting output to head
wc -l *.pdb | sort -n | head -n 1 > lengths.txt	 #stores into lengths.txt
```
---
For further reference, [The Unix Shell](https://swcarpentry.github.io/shell-novice/).

