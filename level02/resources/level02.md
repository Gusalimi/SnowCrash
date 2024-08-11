# level02

`ls -l`
![[ls.png]]

Get it on my own computer:
`scp -P 14242 level02@127.0.0.1:level02.pcap level02.pcap`

Open with wireshark
Right click on one line -> Follow -> TCP Stream
![[Right click.png]]

Show data as UTF-8
![[TCP Stream.png]]
```
ft_wandrNDRelL0L
```
```
Linux 2.6.38-8-generic-pae (::ffff:10.1.1.2) (pts/10)

wwwbugs login: lleevveellXX

Password: ft_wandrNDRelL0L
Login incorrect

wwwbugs login:
```

> The password doesn't work
> I'll use tshark

```
❯ tshark -Tfields -e data -r level02.pcap | tr -d '\n' > data
❯ cat data
fffd25fffc25fffb26fffd18fffd20fffd23fffd27fffd24fffe26fffb18fffb20fffb23fffb27fffc24fffa2001fff0fffa2301fff0fffa2701fff0fffa1801fff0fffa200033383430302c3338343030fff0fffa2300536f646143616e3a30fff0fffa270000444953504c415901536f646143616e3a30fff0fffa1800787465726dfff0fffb03fffd01fffd22fffd1ffffb05fffd21fffd03fffc01fffb22fffa220301000003620304020f05000007621c08020409421a0a027f0b02150f02111002131102ffff1202fffffff0fffb1ffffa1f00b10031fff0fffd05fffb21fffa220103fff0fffa220107fff0fffa2103fff0fffb01fffd00fffe22fffd01fffb00fffc22fffa220303e20304820f07e21c08820409c21a0a827f0b82150f82111082131182ffff1282fffffff00d0a4c696e757820322e362e33382d382d67656e657269632d70616520283a3a666666663a31302e312e312e322920287074732f3130290d0a0a010077777762756773206c6f67696e3a206c006c6500657600766500656c006c5800580d01000d0a50617373776f72643a2066745f77616e64727f7f7f4e4452656c7f4c304c0d000d0a01000d0a4c6f67696e20696e636f72726563740d0a77777762756773206c6f67696e3a20% 
```

```
❯ python2.7
Python 2.7.18 (default, Mar  6 2023, 08:55:32) 
[GCC 12.2.1 20230201] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> "fffd25fffc25fffb26fffd18fffd20fffd23fffd27fffd24fffe26fffb18fffb20fffb23fffb27fffc24fffa2001fff0fffa2301fff0fffa2701fff0fffa1801fff0fffa200033383430302c3338343030fff0fffa2300536f646143616e3a30fff0fffa270000444953504c415901536f646143616e3a30fff0fffa1800787465726dfff0fffb03fffd01fffd22fffd1ffffb05fffd21fffd03fffc01fffb22fffa220301000003620304020f05000007621c08020409421a0a027f0b02150f02111002131102ffff1202fffffff0fffb1ffffa1f00b10031fff0fffd05fffb21fffa220103fff0fffa220107fff0fffa2103fff0fffb01fffd00fffe22fffd01fffb00fffc22fffa220303e20304820f07e21c08820409c21a0a827f0b82150f82111082131182ffff1282fffffff00d0a4c696e757820322e362e33382d382d67656e657269632d70616520283a3a666666663a31302e312e312e322920287074732f3130290d0a0a010077777762756773206c6f67696e3a206c006c6500657600766500656c006c5800580d01000d0a50617373776f72643a2066745f77616e64727f7f7f4e4452656c7f4c304c0d000d0a01000d0a4c6f67696e20696e636f72726563740d0a77777762756773206c6f67696e3a20".decode("hex")
'\xff\xfd%\xff\xfc%\xff\xfb&\xff\xfd\x18\xff\xfd \xff\xfd#\xff\xfd\'\xff\xfd$\xff\xfe&\xff\xfb\x18\xff\xfb \xff\xfb#\xff\xfb\'\xff\xfc$\xff\xfa \x01\xff\xf0\xff\xfa#\x01\xff\xf0\xff\xfa\'\x01\xff\xf0\xff\xfa\x18\x01\xff\xf0\xff\xfa \x0038400,38400\xff\xf0\xff\xfa#\x00SodaCan:0\xff\xf0\xff\xfa\'\x00\x00DISPLAY\x01SodaCan:0\xff\xf0\xff\xfa\x18\x00xterm\xff\xf0\xff\xfb\x03\xff\xfd\x01\xff\xfd"\xff\xfd\x1f\xff\xfb\x05\xff\xfd!\xff\xfd\x03\xff\xfc\x01\xff\xfb"\xff\xfa"\x03\x01\x00\x00\x03b\x03\x04\x02\x0f\x05\x00\x00\x07b\x1c\x08\x02\x04\tB\x1a\n\x02\x7f\x0b\x02\x15\x0f\x02\x11\x10\x02\x13\x11\x02\xff\xff\x12\x02\xff\xff\xff\xf0\xff\xfb\x1f\xff\xfa\x1f\x00\xb1\x001\xff\xf0\xff\xfd\x05\xff\xfb!\xff\xfa"\x01\x03\xff\xf0\xff\xfa"\x01\x07\xff\xf0\xff\xfa!\x03\xff\xf0\xff\xfb\x01\xff\xfd\x00\xff\xfe"\xff\xfd\x01\xff\xfb\x00\xff\xfc"\xff\xfa"\x03\x03\xe2\x03\x04\x82\x0f\x07\xe2\x1c\x08\x82\x04\t\xc2\x1a\n\x82\x7f\x0b\x82\x15\x0f\x82\x11\x10\x82\x13\x11\x82\xff\xff\x12\x82\xff\xff\xff\xf0\r\nLinux 2.6.38-8-generic-pae (::ffff:10.1.1.2) (pts/10)\r\n\n\x01\x00wwwbugs login: l\x00le\x00ev\x00ve\x00el\x00lX\x00X\r\x01\x00\r\nPassword: ft_wandr\x7f\x7f\x7fNDRel\x7fL0L\r\x00\r\n\x01\x00\r\nLogin incorrect\r\nwwwbugs login: '
>>>
```

```
Password: ft_wandr\x7f\x7f\x7fNDRel\x7fL0L
```

```
\x7f => del

password: ft_waNDReL0L
```
#### Pass = ft_waNDReL0L

`su flag02`
`getflag`
![[getflag.png]]

### Flag = kooda2puivaav1idi4f57q8iq