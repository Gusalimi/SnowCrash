# level13

`ls`
![[ls.png]]

![[level13.png]]

Let's disassemble it with gdb
`gdb ./level13`
`disas main`
![[disas main.png]]
> We see that it calls getuid and then compares that result (in eax) with 0x1092 (4242 in hexadecimal)

We will then try to go before the cmp and change the value in eax to 0x1092:
![[gdb.png]]
### Flag = 2A31L79asukciNyi8uppkEuSx