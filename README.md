# Named pipe utilities

This is a very small collection of very small command-line utilties
that use named pipes for communication, typically between different
terminal sessions.

## put and take

The `put`(1) command writes its standard input to a named pipe;
the `take`(1) command writes to standard output from a named pipe.

### Examples

In one terminal,

> `$ echo 'I am an example!' | put`  
> `$`

In another terminal,

> `$ take`  
> `I am an example!`  
> `$`

`take`(1) can also be used in conjuction with `makenamedpipe`(1)
to split the live standard output and standard error of a command
across terminal windows. In one terminal,

> `$ program 2>$(makenamedpipe)`  
> _standard output of program ..._

In another terminal,

> `$ take`  
> _standard error of program ..._

## freeze and thaw

The `freeze`(1) command waits for `thaw`(1) to be run, then exits.
