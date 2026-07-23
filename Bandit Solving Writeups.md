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
