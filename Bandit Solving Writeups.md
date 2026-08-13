# Bandit Solving Writeups :

# Bandit0 :

Bandit 0 is just a text file which you have to use cat on. For eg. the text file is named “readme”, you just have to type “cat readme” into the terminal and you’ll get the flag.

# Bandit1 :

Bandit 1 is a bit more complicated than bandit 0 because the file which we have to print out using cat is named “-”. Most commands take “-” as a delimiter for a flag, and hence have difficulty working with files named “-”. The solution for this is using “cat ./”-””. This reads out the path of the file “-”, and hence cat can successfully print out the file.

# Bandit2 :

Bandit 2 is unsurprisingly more complicated than Bandit 1, with it now having spaces in its filename. The filename is —spaces in this filename—. To access this file’s contents using cat, we have to use the command cat ./”—spaces in this filename—”. The ./ and the “” are required to handle the double dashes and the spaces in the filename.

# Bandit3 :

Bandit 3 is a bit confusing on first sight, but becomes very simple pretty quick. There are no files visible when we use ls in the directory inhere, but when we use ls with the flag -a (ls -a, which is used to show all files and directories, even hidden ones), it shows a hidden text file, upon which we can easily use cat on.

# Bandit4:

Bandit 4 gives us a bunch of files, out of which only one is a human-readable text file, and that file contains the flag. We could print the contents of every single file and get the flag, but that would be a lot of typing. We could hence use the ‘file’ command, which gives us the file-type of the file. Of course, using the ‘file’ command on every single file in the directory is again tedious work, and hence we use the ‘*’ operator, which runs the command on every file in the directory. So we use file ./* to find out the file type of every file, and then use cat to print the contents of the file that has the text type.

# Bandit5 :

Bandit 5 fives us a lot of directories, each with a lot of files, from which only one has the flag. However, they give us some hints about the file itself, it is human readable, is exactly 1033 bytes in size, and is not an executable file. For this challenge, we are going to use the ‘find’ command. The find command is a very powerful command used to find files or directories, with a lot of options and ways to use it.

We are going to use “find -size 1033c ! -executable”

Let us review this command. The find command is taking the parameter size, which allows us to search for files with a particular size. -size 1033c searches for files with exactly 1033 characters or bytes, which is what we want.  if we want a file more than 1033 bytes, we can use -size +1033c flag, and for less than 1033 bytes, we can use -size -1033c flag. ! -executable is telling it that the file should NOT be an executable file (indicated by the ! operator).

# Bandit6 :

Bandit 6 is pretty similar to bandit 5, where we have a lot of files and directories to search through. This time, the hint for our file is 33 bytes in size, owned by group bandit6, and owned by user bandit7. We’re going to use the command “find -size 33c -group bandit6 -user bandit7”. This file command takes the flags -size 33c, which searches for a file that is 33 bytes in size, -group bandit6 which searches for a file owned by group bandit6, and -user bandit7 which searches for a file owned by user bandit7.

Once we use this command, we’re going to get a lot of results as lot of files are 33 bytes in size, and owned by group bandit6 and user bandit7. However, most of them are permission denied results, and only one should give us the path to the actual file. search for it and you’ll get the path to the file, and use cat on the path to get the flag.

# Bandit7 :

Bandit 7 gives us a single text file in which our flag is there. However, the text file is an incredibly large txt file, with a lot of words and flags next to the words. However, the hint we have is, out flag is next to the word “millionth”. The command we are going to use is grep, which is an incredibly powerful tool to search through text. grep’s basic command format is grep [word/pattern] [file].

We are going to use the command “grep millionth data.txt”, which is going to search for the line in the txt file that has the word millionth. We’ll get the flag next to the word millionth.

# Bandit8 :

Bandit 8 is where we introduce ourselves to a concept called piping, where we can use two commands together by sending the output of one command to the second command. Let us first look at the challenge itself. We are given a text file, which contains a lot of strings, and our flag is one of them. The hint given to us is that our flag is the only string that is not repeated in the file.

There is a command called uniq, which allows us to print only unique lines, however there is a catch, it can only detect duplicate lines if they are next to each other. This is an issue for us as in the txt file, the strings are in a random order. Luckily however, there is a command that sorts contents of a file for us, called sort. sort sorts the file, and puts all duplicate strings next to each other, which then makes it possible for us to use uniq on.

To use both sort and uniq together, we are going to use the | operator, which is used for pipinh.

the command is “sort data.txt | uniq -u”

this command sorts data.txt, and then because of the | operator, sends the sorted output to the uniq command. we use uniq -u to print only unique strings (-u flag is to tell uniq to print only unique strings), which then prints the only unique string in the text file, which is our flag.

# Bandit9 :

Bandit 9 gives us a binary file, through which we have to search for our flag. The hint which we are given is that that there are several ‘=’ characters before our flag.

to search through a binary file using grep, we have to use the -a flag before the file name.

the command we are going to use is “grep === -a data.txt” The -a flag allows to grep through the binary file like it is a normal text file. i gave 3 ‘=’ characters as the pattern to search for as they mentioned that there are several ‘=’ characters before the flag.

once we use this command, we are given a few results containing a lot of ‘=’ characters. However, only one of them is clearly a flag, and hence we get our flag.

# Bandit10 :

We are given only one file, and it is revealed to be a Base64 encrypted file. The command ‘base64’ is used to both encrypt and decrypt files into the base64 format.

We use the command “base64 -d data.txt”. the -d flag is to indicate that we are decrypting from base64 and not encrypting. We recieve the flag after using this command.

# Bandit11:

This is probably going to be the most confusing one out of the ones we faced till now, so its going to be a bit hard, but don’t give up. We are given a text file, that is encrypted using the caesar cipher.

We are going to use a command ‘tr’ that takes in text, and replaces characters according to the characters we want.

for eg. cat data.txt | tr -”a-m” “n-z”

this command takes the text, replaces every character from a-z with n-z, and is a very basic application of tr.

the command we are going to use is cat data.txt | tr “a-zA-Z” “n-za-mN-ZA-M”

It takes “a-zA-Z” as one array, and “n-za-mN-ZA-M” as the second array, both having 52 characters.

a-z has 26 characters, and n-za-m has 26 characters. a-m(the first 13 characters get replaced by n-z) and n-z(the second 13 characters get replaced by a-m). The same applies for the capital letters A-Z → N-ZA-M (A-Z is 26 characters, N-ZA-M is also 26 characters)

However, there is one simple shortcut instead of getting into all this mess. Just copy the text from using cat on the txt file, go to google, search for a ceaser cipher, post the texct into it, and if asked for a key or a number give 13.

# Bandit12 :

Bandit 12 is a bit of a lengthy, but rather simple challenge. Bandit 12 provides us a file which is a hexdump (think of it like a different format of representing text for now) of a file, which itself has been compressed multiple times through different formats.  

we have to first create a temporary directory and copy the file to that directory as we dont have the necessary permissions to work on the file in this directory. The command we are going to use for this is mktemp -d (This command creates a temporary directory for us and then gives us the path of that directory, which we can copy the file to using cp [file] [path]).

now, we are going to use 5 commands mostly, 1 for checking the file type, 4 for conversion and decompression : file (used for checking file type), xxd (used for converting hexdump into binary and vice-versa), gzip,bzip2 and tar (used for decompression).

after u copy the file into the new temp directory, use xxd -d data.txt > [filename that u want]

this takes the hexdump, makes it raw binary, puts into a new file.

use file command on the new file, and if it is a gzip file, rename it by using mv [filename] [filename].gz, then use gzip -d [filename.gz] (decompresses from gzip format)

This will give u a new file, check its file type by using the file command, if it is a bzip2 file, use mv [filename] [filename.bz2], and then use bzip2 -d [filename.bz2] (decompresses from bzip2 format)

If file type is tar, use the command tar -xf [filename] (dearchives the file we want from this file, -x is for dearchiving and f is specifying that it is a file)

Keep repeating these 3 steps until it tells u that it is ascii text when u use file command on the file, and then use cat on the file to get the flag.

# Bandit13 :

bandit 13 introduces us to public keys and private keys. I won’t get into it too much, but basically, we can log into computers (which have a public key) using our own private keys (as an alternative to using passwords).

The password for the next level is stored in a directory, that can only be read by the user bandit14, but as we are bandit13, we cannot read the password. However, they have given us the private key used to log into bandit14 user. 

What we’re going to do is, we’re going to use cat on the private key file, copy it, exit the current bandit13 session, return to our own desktop, create a new text file, and paste the private key over there.

next, we are going to use a command called chmod, which is used to change the permissions of a file. We are going to use chmod 700 [filename]. This is going to make it that only the user on our desktop has the permission to do anything with the file. (We are using chmod to change permissions, as the next command we are going to use that is ssh, wont accept files that have too many permissions.)

the next command we use is

ssh bandit14@bandit.labs.overthewire.org -p 2220 -i [filename]

(the -i flag is used to provide the private key filename)

This will then log us into the machine as the bandit14 user.

then, we have to change into the directory that has the password by using “cd **/etc/bandit_pass/”**

then, we use cat bandit14, and it will output the password.

# Bandit14 :

Bandit 14 is a simple challenge, that expects us to learn a bit about networking before starting the challenge. 

We have to submit this level’s password to this computer on port 30000 to get the next level’s password (Before starting this chapter, I’d advice you to learn a bit about localhost, ip addresses and ports.)

We are going to use the command nc localhost 30000 (this command allows us to start a communication channel with localhost, which basically means communicating with the same computer, on port 30,000)

then, we are going to take copy this room’s password, and then paste it into the terminal, and then we will receive the password to the next room as the response.

# Bandit15 :

Bandit 15 is a simple challenge as well, that builds upon the experience we got from Bandit14. In Bandit 15, we have to do the same thing as bandit 14, but instead on port 30001, however we have to use ssl/tls encryption (in the previous challenge, we didnt use encryption, which means our communication was potentially insecure and could’ve been spied on).

We are going to use the command openssl (which is a massive cryptographic library used to implement ssl/tls) and the subcommand s_client (which is part of the openssl suite of commands, s_client is used to start an ssl/tls communication session with someone).

The command is openssl s_client -connect localhost:30001
This is going to start an ssl/tls encrypted communication session with port 30001, and then we must paste the password of this level into the terminal, and then we will receive the password to the next level.

# Bandit16 :

Bandit 16 introduces us a new tool called nmap, which lets us scan networks and devices on that network, and it is a very powerful tool. We have to scan ports in range of 31000-32000 on the localhost (which we do using nmap), then find out which service is running on the ports (we need to then start an ssl/tls communication session with a server running on one those ports, and paste the password of the current machine into it).

The first command we are going to use is
nmap localhost -sV -p 31000-32000 [ This command makes nmap scan the localhost’s ports in range 31000-32000, denoted by the flag -p. The -sV flag is to for service detection. It allows us to detect which service is running on which port, which allows us to tell where the server is running on. Once we run this command, we find out that the port is 31970.

The second command we are going to use is 
openssl s_client -connect localhost:31970 -quiet
This allows us to start an ssl/tls certified communication with the localhost on port 31970. The -quiet flag is to help us avoid some trouble due to some possible interactions with s_client’s other functionalities and the password that we are going to paste once the communication has been established.
Once it is established, paste the password and it will return the private key for the next room as a response.

# Bandit17 :

Bandit17 is a very easy challenge, requiring only one simple command. We are given 2 text files, with only 1 line (the password for the next room) being different between them. We are going to use the command 

diff passwords.new passwords.old

it will then output 2 lines, the first line being the difference in passwords.new, and the second line being the difference in passwords.old.

copy the first line, as it is our password for the next room.


# Bandit18 :

Before we get into Bandit18, let us learn a small concept : What is a shell?

In simple words, A shell is simply a software that allows us to interact with our operating system and allows us to perform tasks. All the commands we have typed into the terminal up until now are interpreted by the shell that lies underneath. Most linux computers have a few shells that can be used. The one that is usually being used by default (and is being used in our case as well) is bash.

The .bashrc file that is talked about in the description is a configuration file for the bash shell that is launched everytime we log in using ssh. So, we simply have to log in using ssh with a non bash shell.

All our possible shells are stored in /etc/shells on our linux computer.

type cat/etc/shells to get a list of the possible shells we have. (for eg, i got /bin/sh)

now, we type 

ssh bandit18@bandit.labs.overthewire.org -p 2220 -t “bin/sh” 

this logs in with ssh and using a different shell, which allows us to stay without getting logged out. Once logged in, use ls and cat the readme file that appears for the password.

# Bandit19 : 

Bandit 19 gives us an executable file, that allows us to run commands given to it as the user 20. This is very useful for us, as the password which is stored in /etc/bandit_pass/bandit20 (which the description of the problem tells us) cannot be cat’d by user 19 (which we are right now).
to execute the file, we have to use ./bandit20-do
which then tells us that we can use this file to execute commands as another user. 

we are going to use the command ./bandit20-do cat /etc/bandit_pass/bandit20
which allows us to cat the file as user 20, which will then give us the password for the next round.

# Bandit20: 
Bandit20 gives us a file, that allows us to connect to a port, and if we receive the password to the current room from that port, then this file will output the password to the next room.
We have to first setup something that will output the password to the current room from a port of our choice. For that, we will use netcat/nc’s listener option, which can output a text of our choice.

We will use the command 
echo “password-to-current-room” | nc -p 3333 -l &

piping echo into nc, and the -p flag is to specify the port, and -l flag is to tell that it is to listen.
the & in the end is to tell the shell that the process has to run in the background and not the foreground. without the &, it will run in the foreground and our terminal will become unresponsive to new commands until the nc listener is done. We can give any unused port of our choice for the -p flag by the way.

Once the nc listener is setup, use the command 
./suconnect 3333(or whatever port number you gave)

will output the password of the next room then.

# Bandit21:
Bandit 21 introduces something called cron and cronjobs. Cron is a program that allows us to schedule processes at time intervals of our choice, and cronjobs are processes that cron is running.
We are told to look at /etc/cron.d/ , so that’s exactly what we’ll do.
cd /etc/cron.d to go into the directory, and click ls to see everything in the directory.

We’ll get a lot of cronjob configuration files, but the ones that we’ll look at is cronjob_bandit22 (because we need 22’s password).
We get @reboot bandit22 /usr/bin/cronjob_bandit22.sh & and some more stuff.
this basically means that this job runs at boot of the computer, using bandit22 user’s permissions, and the script that runs is cronjob_bandit22.sh. So, let’s look at the script itself then.
cat /usr/bin/cronjob_bandit22.sh

we then get 2 lines of linux commands that basically tell us this :
the first line with the chmod 644 tell us that there is temp file that is being made which is allowed to be read by everyone.
the second file prints the contents of /etc/bandit_pass/bandit22 (the file that contains the password to 22) into the temp file, so we just have to print the temp file to get the password.

click cat /tmp/tmpfilename and you’ll get the password to 22.

# Bandit22 : 
Mostly the same as Bandit 21, we have to investigate the script that runs as the cronjob.
cd /etc/cron.d to go the cronjobs directory, and click cat cronjob_bandit23 to get more information about the cronjob.
We get to know that it ‘s owned by Bandit23, and it’s path as well. click cat /usr/bin/cronjob_bandit.sh to print the script. whoami is a command that returns the current logged in user, but in the case of cronjobs, they’re executed as the owner of the file (that is bandit23, not 22).
the second line in the script takes the returned name from the whoami command, runs it through an md5 hash algorithm to create a temporary path for a temporary file to store the password of bandit23.

The description tells us to run the command once, so lets do it by clicking /usr/bin/cronjob_bandit23.sh (however, when we run it like this, it runs as bandit22 and not 23, as we are running it and not cron itself, and hence whoami in the script evaluates to bandit 22 and not 23). it tells us that it has created a file and stored the password there. however, the password stored there will be 22’s password as whoami in the script evaluates to 22 and not 23.
TO get the path for 23, we need to use the same temp file path creator that the script uses, so lets type in

echo I am user bandit23 | md5sum | cut -d  ‘  ‘ -f  1


8ca319486bfbbc3663ea0fbe8132634


you will receive this string, and then use cat tmp/8ca319486bfbbc3663ea0fbe8132634, which will give us the password for the next round.

# Bandit23 :
Bandit 23 might be a bit of a headache, but bear with it. Once again we have to deal with cronjobs, so let’s get into it. Let’s cd into /etc/cron.d/ to check out the cronjobs. 
cat cronjob_bandit24 to see who owns the job (it’s obviously bandit24 though) and the path of the script being executed. Cat /usr/bin/cronjob_bandit24.sh to take a look at the script.
To be very honest, I didn’t know understand what this script did, so i just gave it to AI and asked it to tell me what it does. 
Basically, this script has a variable myname, which it stores the return value of whoami into it(which will be bandit24, as it is 24’s cronjob). It then cd’s into a directory called /var/spool/myname/foo, and then executes and deletes every script that is owned by bandit23 in that directory. To get the password, we have to create and place a script owned by bandit23 which cats the contents of 

/etc/bandit_pass/bandit24 (which is where bandit24's password is stored)
Because we don’t have the permissions to create a file anywhere, we have to create a temporary directory (where we will have the permission to do things)
mktemp - d (to create a temp directory, this will create a dir and then return it’s path as well)
nano tempdirpath/bandit23.sh (opens up the text editor for a text file in that directory with the name bandit3.sh)
#!/bin/bash
cat /etc/bandit_pass/bandit24 > tempdirectorypath/password
​
type this code into the text editor. the first line indicates that this is a bash file, and the second line prints the contents of /etc/bandit_pass/bandit24 (the password of bandit 24) into a file called password in the temporary directory.

chmod 777 tempdirectorypath/bandit23.sh (to give full access to all users)
chmod 777 tempdirectorypath (to give full access)
touch tempdirectorypath/password ( i think u can skip this command and the next, because the cat in our script should be able to create the file istelf, considering we chmod 777 the directory itself, but running these commands for safety regardless.)
chmod 777 tempdirectorypath/password
cp tempdirectorypath/bandit23.sh /var/spool/bandit24/foo/bandit23.sh (copies the script into the directory where the scripts are executed by the cronjob)

wait a minute or two, and cat /tempdirpath/password and it’ll print the password. 
