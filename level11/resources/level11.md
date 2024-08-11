# level11

`ls`
![[ls.png]]

`cat level11.lua`
```lua
#!/usr/bin/env lua
local socket = require("socket")
local server = assert(socket.bind("127.0.0.1", 5151))

function hash(pass)
  prog = io.popen("echo "..pass.." | sha1sum", "r")
  data = prog:read("*all")
  prog:close()

  data = string.sub(data, 1, 40)

  return data
end


while 1 do
  local client = server:accept()
  client:send("Password: ")
  client:settimeout(60)
  local l, err = client:receive()
  if not err then
      print("trying " .. l)
      local h = hash(l)

      if h ~= "f05d1d066fb246efe0c6f7d095f909a7a0cf34a0" then
          client:send("Erf nope..\n");
      else
          client:send("Gz you dumb*\n")
      end

  end

  client:close()
end
```

![[Already In Use.png]]

`ps auxf` shows that the program is already launched by flag11

We can then try to connect with `nc`
![[nc test.png]]

We see in the script that the `popen` function will execute a command composed of `echo [the given password] | sha1sum` and then read from it to create the hashed version.

We can exploit that execution by giving `pwned | getflag > /tmp/flag` as the passord (It will execute `echo pwned | getflag > /tmp/flag | sha1sum`)
![[flag.png]]
### Flag = fa6v5ateaw21peobuub8ipe6s