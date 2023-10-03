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
**cd**
with path to a file:
```
[user@sahara ~/lecture1]$ cd /home/lecture1/messages/en-us.txt
bash: cd: /home/lecture1/messages/en-us.txt: Not a directory
[user@sahara ~/lecture1]$ 
```
**ls**
No arguments: 
```
[user@sahara ~/lecture1]$ ls
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$ 
```
**ls**
With path to a directory:
```
[user@sahara ~/lecture1]$ ls /home/lecture1
Hello.class  Hello.java  messages  README
[user@sahara ~/lecture1]$ 
```
**ls**
With path to a file:
```
[user@sahara ~/lecture1]$ ls /home/lecture1/messages/en-us.txt
/home/lecture1/messages/en-us.txt
[user@sahara ~/lecture1]$ 
```
**cat**
No arguments: 
```
[user@sahara ~/lecture1]$ cat
```
**cat**
With path to a directory:
```
[user@sahara ~/lecture1]$ cat /home/lecture1
cat: /home/lecture1: Is a directory
[user@sahara ~/lecture1]$ 
```
**cat**
With path to a file:
```
[user@sahara ~/lecture1]$ cat /home/lecture1/messages/en-us.txt
Hello World!
[user@sahara ~/lecture1]$
```
