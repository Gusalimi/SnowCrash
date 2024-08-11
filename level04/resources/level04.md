# level04 

![[ls.png]]

`cat level04.pl`
```perl
#!/usr/bin/perl
# localhost:4747
use CGI qw{param};
print "Content-type: text/html\n\n";
sub x {
  $y = $_[0];
  print `echo $y 2>&1`;
}
x(param("x"));
```
> Creates a webpage on localhost:4747/level04.pl and echoes the x parameter


![[Webpage.png]]
*Port forwarded 4747 to 34242*

### Flag = ne2searoevaevoem4ov4ar8ap