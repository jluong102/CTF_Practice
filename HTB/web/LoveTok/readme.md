This challenge can be solved using a RCE that can be found 
in the format parameter.
Taking a quick look through the code you will find TimeModel.php  
In this php file you will find the getTime function which 
will print a time to the web page.

After some testing we can find that we are able to use the "\`" 
to evaluate system commands.  Combining this with the `print` command 
we can run commands on the server.  
Using this we can get the flag with a payload such as 

    ?format=${print(`cat ../flag2GPsC\`)
