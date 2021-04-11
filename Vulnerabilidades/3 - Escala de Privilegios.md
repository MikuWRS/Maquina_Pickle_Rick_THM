# Escalada de privilegios a Root y obtención de la tercera flag

Para suerte nuestra, el usuario y contraseña utilizado en [[1 - Ingreso y manipulación en portal.php]] es el "usuario root" por lo que nos bastaria solo con realizar un `sudo -i` para que se nos asignen los privilegios de root.

### Flag
Por lo anterior, si realizamos un `ls` podemos ver que existe un fichero llamado "3rd.txt" y si le realizamos un `cat` tendremos nuestra tercera flag y la máquina estaria resuelta.