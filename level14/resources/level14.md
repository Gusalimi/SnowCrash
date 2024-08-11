# level14

Nothing in ~ and nothing with advanced search (`find`, `netstat`, `ps`)

In the previous exercises we exploited a binary with `gdb` by changing the registers to appear as another UID. Let's try to do the same with getflag.

`gdb getflag`
`run`
![[Reverse.png]]
`disas main`
![[ptrace.png]]

We see that the binary is protected against debugging by using ptrace and checking its value (ptrace can be called only once per execution so if gdb called it, the call in the main will fail).

We can see with a breakpoint that it's indeed -1:
![[eax = -1.png]]

So let's set to 0 with `p $eax=0`

We now have to change the UID.
Let's first find the call to `geteuid` with `(gdb) disas main`:
![[getuid.png]]

We'll go before the first `cmp` to change it:
`b *main+452`
`continue`
We can see that our current id is 2014 with `p $eax` returning 2014

To know the UID of flag14 we can `cat /etc/passwd` (outside of gdb)
We find this line `flag14:x:3014:3014::/home/flag/flag14:/bin/bash` so the UID of flag14 is 3014. Let's change it :
`(gdb) p $eax=3014`
`continue`
![[Flag.png]]

### Flag = 7QiHafiNa3HVozsaXkawuYrTstxbpABHD8CPnHJ