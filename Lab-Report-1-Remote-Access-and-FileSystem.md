# Lab Report 1
Ryan Livengood
10/3/2023
P
CSE 15L

## Command tests
**cd**
<br />
no arguments: 
```
[user@sahara ~]$ cd
[user@sahara ~]$ 
```
This command was run in the home directory. I got this output because cd does not print anything, it changes the working directory. This output is an error because no directory was provided, meaning there was no directory to change to.
**cd**
with path to a directory:
```
[user@sahara ~]$ cd /home/lecture1
[user@sahara ~/lecture1]$ 
```
This command was run in the home directory. I got this output because cd does not print anything, it changes the working directory. Although it did not print anything, the path has changed, where /lecture1 was appended to the end. This means that the working directory is now lecture1. No error occurred.
**cd**
with path to a file:
```
[user@sahara ~/lecture1]$ cd /home/lecture1/messages/en-us.txt
bash: cd: /home/lecture1/messages/en-us.txt: Not a directory
[user@sahara ~/lecture1]$ 
```
This command was run in the lecture1 directory. I got this output because there was an error. en-us.txt is not a directory, so cd was unable to change to it. This resulted in it printing the input back out, and keeping the working directory the same.
**ls**
No arguments: 
```
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$ 
```
This command was run in the lecture1 directory. It output a list of all the files and directories in lecture1, because the function of ls is to list all these things for the working directory. There was no error here.
**ls**
With path to a directory:
```
[user@sahara ~/lecture1]$ ls /home/lecture1
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$ 
```
This command was run in the lecture1 directory. Since the directory we input is the same as the working directory, it had the same output as our previous call. No error here.
**ls**
With path to a file:
```
[user@sahara ~/lecture1]$ ls /home/lecture1/messages/en-us.txt
/home/lecture1/messages/en-us.txt
[user@sahara ~/lecture1]$ 
```
This command was run in lecture1 directory. Similarly to the final call of cd, ls does not work in files because files do not hold directories or other files, therefore there was nothing to list. This resulted in an error where it output what we input.
**cat**
No arguments: 
```
[user@sahara ~/lecture1]$ cat
```
This command was run in the lecture1 directory. The function of cat is to print the data in a file. Since we did not provide a file, nothing was output. This is an error, and as a result nothing was output.
**cat**
With path to a directory:
```
[user@sahara ~/lecture1]$ cat /home/lecture1
cat: /home/lecture1: Is a directory
[user@sahara ~/lecture1]$ 
```
This command was run in the lecture1 directory. Since we did not provide a file, but rather a directory, cat ran into an error. It handled the error by correctly outputting that we provided a directory instead of a file.
**cat**
With path to a file:
```
[user@sahara ~/lecture1]$ cat /home/lecture1/messages/en-us.txt
Hello World!
[user@sahara ~/lecture1]$
```
This command was run in the lecture1 directory. We provided the file en-us.txt, and cat output the contents of that text file. Since we used the command correctly. there was no error.

