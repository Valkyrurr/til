#wall
 
### TLDR  

Write a message on the terminals of users currently logged in.
 
   - Send a message:
     `echo "message" | wall`
 
   - Send a message from a file:
     `wall file`
 
   - Send a message with timeout (default 300):
     `wall -t seconds file`
     
### DESCRIPTION  

`wall` displays a message, or the contents of a file, or otherwise its standard input, on the terminals of all currently logged in users.  
The command will wrap lines that are longer than 79 characters.  Short lines are whitespace padded to have  79  characters.  
The  command  will always put a carriage return and new line at the end of each line.  

Only the superuser can write on the terminals of users who have chosen to deny messages or are using a program which automatically denies messages.    

Reading from a file is refused when the invoker is not superuser and the program is suid or sgid.  

### OPTIONS  
   -n, --nobanner
          Suppress the banner.

   -t, --timeout timeout
          Abandon the write attempt to the terminals after timeout seconds.  This timeout must be a positive integer.  The default value is 300
          seconds, which is a legacy from the time when people ran terminals over modem lines.

   -V, --version
          Display version information and exit.

   -h, --help
          Display help text and exit.