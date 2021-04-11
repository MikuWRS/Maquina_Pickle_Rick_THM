# Enumeración de servicios encontrados

Para la enumeracion de servicios utilizaremos el siguiente comando:

```bash
> nmap -sC -sV -p20,80 IP_MAQUINA
```

Donde:
- `-sC` : Nos permite lanzar una serie de script basicos para enumeración.
- `-sV`: Nos permite detectar la version y servicios que corren.
- `-p20,80`: Son los puertos (`-p`) a los que se les realizará el escaneo.
- `IP_MAQUINA`: Es la direccion IP de la máquina objetivo.