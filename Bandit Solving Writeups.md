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
