This is a reversing challenge based on a random number.
Starting the anaylsis of we can start of by taking look at the strings.
Only intresting string found is "SuperSeKretKey".
Disassembling this, we can take a look at the main function (0x40085d) 
and see that there are two strcmps.  The first one checks to see 
if the user enters "SuperSeKretKey" as the first input.  If that 
input is entered correctly then the program will prompt for a second 
user input looking to match the output of the 0x40078d function. 
Taking a look at this function we can see that it will create an output 
using a randomly generated number based on the time.  Looking a little 
ahead, we can see that the function 0x0400978 is called if the our second 
input matches the random output.  Looking at this function we can see that it
likly is going to print the flag char by char. 

Since we know at this point that we should be able to do this all off the local 
binary (being that there is no remote address to connect to), we can use some 
gdb magic to call the function that prints the flag.

* Run the program in gdb
* Set a breakpoint after the second user input
* Start the program and enter "SuperSeKretKey" for the first prompt
* Once the breakpoint is hit, jump to 0x0400978

