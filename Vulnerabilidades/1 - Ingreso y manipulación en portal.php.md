# Obtención de acceso a consola remota
Mediante la página `IP_MAQUINA/login.php` podemos acceder a un login donde nos piden un usuario y una clave. Previamente en el [[1 - Reconocimiento Web]] pudimos encontrar un usuario llamado **R1ckRul3s** y dentro del archivo "robots.txt" mencionado en  [[4 - Rutas y Archivos]] encontramos un texto que dice **Wubbalubbadubdub**.

Probando estos textos como usuario y contraseña respectivamente, se consiguio acceso a un página llamada `IP_MAQUINA/portal.php` donde hay acceso a un panel de comando como se muestra a continuación:

![image](https://github.com/MikuWRS/Maquina_Pickle_Rick_THM/blob/main/imgs/Pasted%20image%2020210410185224.png)
[//]: # (![[Pasted image 20210410185224.png]])

---
# Probando comandos en la consola remota
Utilizando el comando de consola `whoami` obtenemos como respuesta que somos el usuario "www-data". Por lo tanto, ya podemos decir que estamos dentro del sistema.

![[Pasted image 20210410185344.png]]

Luego realizando un `ls` para ver contenidos de la carpeta actual podemos ver lo siguiente:

![[Pasted image 20210410185424.png]]

De esto existen 2 archivos que podrian ser interesantes para resolver la máquina. Uno es "Sup3rS3cretPickl3Ingred.txt" y "clue.txt". Lamentablemente no podemos ver el contenido de estos archivos ya que el comando `cat` se encuentra deshabilitado como se muestra a continuación:

![[Pasted image 20210410190045.png]]

Sin embargo, podemos realizar un pequeño truco para burlar este problema. 

---

# Lectura de la primera flag
Bash permite utilizar la siguiente estructura para los resolutores de comandos `/????/????`, por lo tanto podemos aplicar esta forma a la direccion donde se encuentra localizado el comando `cat`,  asumiendo que este se encuentra en la dirección `/bin/cat` ejecutamos el siguiente código:

```bash
> /???/??t Sup3rS3cretPickl3Ingred.txt
```

Ejecutado este comando nos responde con el siguiente mensaje donde podemos ver nuestra primera flag de la máquina:

![[Pasted image 20210410190742.png]]

---

Realizando el mismo proceso con el archivo "clue.txt" obtenemos como respuesta *"Look around the file system for the other ingredient."*
Por lo que se proseguirá buscando alguna información relevante en "portal.php"


