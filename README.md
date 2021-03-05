# custom_shell

Simple shell program that can processes commands.

## Default command set
ls, cd, help, exit

- ls : The readdir function in the structure of the dirent.h header file is used to read and print the file information in the current directory.
- cd : Use the chdir function to change the current directory to the address entered for the second factor.
- help : Show shell's defualt command
- exit : Exit shell



## Shell logic

- exec_handler() : tokenizes and saves the command line received through the tokenizer.

- parse_default() : Verify that the command is the default command, and if it is included in the default set of commands, use exec_default() to execute the corresponding function for the command. If it is not the default command, create a child process through the fork.

- parse_Redirect() : Verify that it contains a factor (>) that dictates redirect, and if so, runexec_redirect() to override the output with the factor that follows it.

- parse_Background() : Verify that it contains a factor (&) that directs the background action, and, if so, prevents the parent process from running wait() to perform background processing of the child process.
