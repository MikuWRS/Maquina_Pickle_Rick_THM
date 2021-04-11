Mediante la herramienta `gobuster` se realizó un escaneo para obtener posibles rutas y/o archivos que se encuentren alojados en la dirección IP.

```bash
> gobuster dir -u IP_MAQUINA -w /usr/share/wordlists/disb/common.txt
```

Obteniendo el siguiente resultado:

```bash
==============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
==============================================================
[+] Url:                     http://IP_MAQUINA
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Timeout:                 10s
==============================================================
2021/04/10 17:37:36 Starting gobuster in directory enumeration mode
==============================================================
/.hta                 (Status: 403) [Size: 292]
/.htpasswd            (Status: 403) [Size: 297]
/.htaccess            (Status: 403) [Size: 297]
/assets               (Status: 301) [Size: 315] [-->http://10.10.203.110/assets/]
/index.html           (Status: 200) [Size: 1062]
/robots.txt           (Status: 200) [Size: 17]
/server-status        (Status: 403) [Size: 301]
==============================================================
2021/04/10 17:40:06 Finished
==============================================================
```

Paralelamente se ejecuto un escaneo con la herramienta `nmap` para descubrir posibles archivos o rutas que `gobuster` no haya podido detectar, para ello se realizó el siguiente comando:

```bash
> nmap --script http-enum -p80 IP_MAQUINA
```

Donde se obtuvo el siguiente resultado:

```bash
Starting Nmap 7.90 ( https://nmap.org ) at 2021-04-10 18:36 -04
Nmap scan report for IP_MAQUINA
Host is up (0.31s latency).

PORT   STATE SERVICE
80/tcp open  http
| http-enum:
|   /login.php: Possible admin folder
|_  /robots.txt: Robots file

Nmap done 1 IP address (1 host up) scanned in 30.76 seconds
```

---
Dentro del archivo **robots.txt** podemos encontrar un texto que dice:

- Wubbalubbadubdub

El cual podria ser un posible usuario o clave.