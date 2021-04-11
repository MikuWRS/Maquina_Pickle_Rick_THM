# Reconocimiento de puertos por TCP

A continuación, se detalla la metodología llevada a cabo para realizar una enumeración de puertos TCP.

Para ello se deberá ejecutar el comando `nmap` de la siguiente forma:

```bash
> nmap -p- -sS --min-rate 5000 --open -vvv -n -Pn IP_MAQUINA
```

Donde:
- `-p-`: Indica que se escanearan los 65535 puertos.
- `-sS`: Indica que se realizara un escaneo SYN.
- `--min-rate 5000`: Indica que el escaneo no puede emitir paquetes más lentos que 5000 paquetes por segundo.
- `--open`: Indica que solo muestre los puertos que estan en estado "open".
- `-vvv`: Se utiliza para que arroje más información al momento del escaneo.
- `-n`: Se utiliza para que el escaneo no realice resolución de DNS.
- `-Pn`: Se utiliza para que no se realice Host Discovery.
-  `IP_MAQUINA`: Corresponde a la dirección IP de la máquina objetivo.