# level09

`ls`
![[ls.png]]

`cat token` gives printable and unprintable characters
![[cat.png]]

By testing we can see that `./level09` applies a caesar cypher with a shift that begins at 0 and increases at each character
![[test.png]]

Let's print the ascii codes first
`od -t u1 -An token` *(-t u1 for unsigned char and -An to get only data and no adresses)*
![[od.png]]

We can now decript with a little python script
```python
token = [102, 52, 107, 109, 109, 54, 112, 124, 61, 130, 127, 112, 130, 110, 131, 130, 68, 66, 131, 68, 117, 123, 127, 140, 137, 10]
new = []
for i in range(len(token)):
    new.append(token[i] - i)
for elem in new:
    print(elem, end=' ')
```
![[python.png]]

And using an ASCII to Text we get **f3iji1ju5yuevaus41q1afiuq**
`su flag09`
`getflag`
![[getflag.png]]

### Flag = s5cAJpM8ev6XHw998pRWG728z