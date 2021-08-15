This is a basic pwn challenge.
Taking a quick look at the binary, we can find a function called vuln.
In here there is a buffer overflow that can exploited.
We can see that there is a space of 0xB8 bytes able to be written 
before ebp. Taking a further look at the binary, we can find a 
function flag.  In this function we can see that it reequires to parameters.
One at ebp + 0x4 and one at ebp + 0x8.  If both of these parameters are set 
correctly the function will print the flag.

Knowning this we can construct our exploit with the following steps:
	* Overflow the buffer (0xB8 bytes
	* Overwrite ebp (add another 4 bytes)
	* Jump to flag address
	* Add 4 bytes to get to the location of the first parameter
	* Add the bytes of 0xdeadbeef to the payload (parameter 1)
	* Add the bytes of c0ded00d to the payload (parameter 2)
