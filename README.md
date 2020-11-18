# Comandos curiosos de Linux
## chattr<p>
 
Cambia los atributos de un fichero en un sistema de ficheros de Linux, podemos usarlo para proteger archivos o directorios de "desastres no deseados" y otras cosas más interantes. Sigue leyendo y lo averiguarás.<p>
La sintaxis del comando, aunque depende de las distribuciones de Linux, sería:<p>
``` Usage: chattr [-pRVf] [-+=aAcCdDeijPsStTuF] [-v version] files...```<p>

#### Opciones:<p>
- '-R': Aplica recursividad a los directorios y sus contenidos. Se ingnora los enlaces simbólicos.<p>
- '-V': Verbose.<p>
- '-p': establece un número de proyecto a un fichero.<p>
- '-f': suprime la mayoría de mensajes de error.<p>
- '-v': versión<p>

#### Modo:
Los operadores (**+-=**):<p>
- '+': añade un o más atributos a los que tiene el fichero seleccionado.<p>
- '-': elimina uno o más atributos del fichero.<p>
- '=': hace que sean solo esos atributos.<p>

Atributos (**aAcCdDeijPsStTuF**):<p>
- a: Un fichero con el atributo 'a' establecido solo se puede abrir en modo añadir para escritura.<p>
- A: Si se establece este atributo, el atime ( fecha de último acceso ) del fichero no se modifica. Interesante si vas a hacer algo :sunglasses: <p>
- c: Cuando estableces este atributo el fichero es comprimido automáticamente en el disco por el kernel. Cuando se lee el fichero, éste se descomprime.<p>
- d: Si se establece este atributo no se hará backup del fichero cuando se utiliza el comando dump.<p>
- D: Cuando se modifica un directorio con este atributo, los cambios se escriben sincrónicamente en el disco.<p>
- i: Este es el mejor de todos, si estableces este atributo, un fichero no puede ser borrado, renombrado, no puedes crear enlaces simbólicos y los metadatos del fichero no pueden ser alterados y no se puede abrir en modo escritura.<p>
- s: Cuando se elimina un archivo con el atributo 's' establecido, sus bloques se ponen a cero por lo que no podrás volver a recuperar ese fichero. Forma segura de eliminar datos :purple devil:<p>
- S: Cuando se modifica un archivo con el atributo 'S', los cambios se escriben sincrónicamente en el disco sin esperar al S.O. Esto es equivalente al 'sync'.<p>
- u: Cuando un archivo con este atributo es eliminado, sus contenidos son guardados permitiendo recuperar el archivo con herramientas de recuperación.<p>

#### Ejemplos:
*Hacemos que el fichero test.txt sea inmutable, con + activamos y con - quitamos esa opción*
```
$touch test.txt
$lsattr test.txt 
-------------------- test.txt
$sudo chattr +i test.txt
$lsattr test.txt 
----i--------------- test.txt
$sudo chattr -i test.txt
$lsattr test.txt 
-------------------- test.txt
```
