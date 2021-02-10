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

![secret](images/secret.png)

Download image, and use steghide

```bash
steghide extract -sf find.jpg
```

![steghide](images/steghide.png)

Go to imgur

![imgur](images/imgur.png)

Download barcode, and [decode](https://zxing.org/w/decode.jspx)

![decode](images/decode.png)

Login ssh with this data

![user](images/user.png)

Use [CVE-2021-3156 PoC by blasty](https://github.com/blasty/CVE-2021-3156) or [Sudo 1.9.5p1 - 'Baron Samedit ' Heap-Based Buffer Overflow Privilege Escalation](https://www.exploit-db.com/exploits/49521) for PrivEsc

![httpserver](images/httpserver.png)

![download](images/download.png)

Compile the exploit

```
cd exploit
make
```

![make](images/make.png)

Run the exploit

![sudo](images/sudo.png)

Capture the flag

![root](images/root.png)
