Crear un Bash script que te permita cambiar entre diferentes opciones:
1. Crear un archivo dentro de algún directorio que se encuentre en `$HOME`:
```sh
./exercise.sh 1\n Downloads \n file.txt
```
2. Instalar un programa con su administrador de paquetes:
```sh
./exercise.sh 2\n cmatrix
```
3. Buscar un archivo (puede ser usando `find`, por ejemplo):
```sh
./exercise.sh 3\n Hola.txt
```

Lugares útiles para buscar/leer
1. `man find`
Intentar buscar por 'pattern' y eligir la opción para buscar archivos
2. Usar `read` para leer input
3. `man test`
En scripts se puede usar como `[ condition ]`
Buscar por *file* (no es lo mismo que *FILE*)