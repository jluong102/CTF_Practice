This challege can be solved using a format string exploit.

We start by taking a look at the binary and find a few menus.
Looking through these menu functions there is little to be found.
The menu function that we primarly want to look is car_menu.
In here, towards the second half of the funciton, we see the flag is loaded in.
Right after this function we see that there is a string created off of user 
input that is then repeated out via printf directly. Since the flag is never 
printed to stdout we can use the format string here.

Steps to solve:
* Enter any fluff for the first two inputs
* Enter 2
* Enter 2 
* Enter 1
* For the win message enter a bunch of "%p" to print the pointers 
	from the stack
* Strip the "0x" and "(nil)" from the output returned
* Convert the remaining output to ascii
* Search for a string the represents the flag
	* This string will be in sets of 4 bytes
* Reverse the 4 byte string sets
