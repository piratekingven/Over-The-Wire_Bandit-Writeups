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