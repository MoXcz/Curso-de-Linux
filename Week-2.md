```sh
sudo nano /etc/sudoers
```

---
Google Chrome:

```sh
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb
rm google-chrome-stable_current_amd64.deb
google-chrome
```

---

Visual Studio Code:

```sh
wget -O code-latest.deb 'https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64'
sudo apt install ./code-latest.deb
rm code-latest.deb
code
```

---

- Shell
- Programs
- Utilities

---

Filosofía Unix

- Cada programa hace **UNA** sola cosa, y la hace bien
- El *output* de un programa puede ser usado como el *input* de otro programa
- Las herramientas hacen lo que deben de hacer

---

Concatenación de archivos y enviarlos al *Standard Out*

```sh
cat file1 file2 file3
```

---

```sh
sudo apt install bsdmainutils
ncal
date
```

---

```sh
ls
mkdir linux_test
echo hola
echo hola > hola.txt
cat hola.txt
echo mundo >> hola.txt
wc -c < hola.txt
```

---

```sh
echo adios > adios.txt
cat hola.txt adios.txt > ambos.txt
```

---

- `>`. Redirige el *Standard Out* a un archivo (lo sobrescribe).
- `>>`. Redirige el *Standard Out* al final de un archivo.
- `<`. Redirige el *Standard In* de un archivo a un comando.

---

Es mas fácil agregar al final de un archivo que al inicio:

```sh
(echo al inicio; cat hola.txt) > hola.txt_ && mv hola.txt{_,}
```

Para agregar al inicio es necesario primero recorrer todo el contenido del archivo hacia abajo y después insertar.

---

```sh
echo whatever >> hello.txt
(echo at the beginning; cat hello.txt) > hello.txt_
echo hello.txt{_,}
```

---

- `Control-X`
- `Control+X`
- `Ctrl-X`
- `Ctrl+X`
- `^X`
- `C-x`

---

- `C-d`. Salir de un programa *delicadamente*
- `^c`. Cerrar forzosamente.
- `reset`. En caso de cualquier error.

---

- Comandos (*commands*). Programas que siguen la filosofía de Unix.
- Argumentos (*arguments*). Opciones y/o archivos para el comando.
- Opciones (*options* / *flags*). Modificaciones para el comando.

---

- `cd` (*Change Directory*). Moverse en la terminal (lo que realmente pasa es que se cambia el *Current Working Directory* bajo el que esta trabajado shell (Bash).
- `pwd`. *Print Working Directory*

---

- `rm`. Eliminar archivos (`-r` para eliminar directorios)
- `rmdir`. Eliminar directorios vacíos

---

Crear directorios y especificaciones con expansion de llaves (*brace expansion*): 

```sh
mkdir -p dirs/dir{0..100..2}
cd dirs/
rm -r dir{0..100..2}
cd
rm -r dirs/
```

---

```sh
sudo apt install neovim
echo $HOME
cd
cd Documents/
nvim hola.txt_
cd ../linux-test
cp -r ~/Documents/* .
```

---

Si el ultimo argumento de `cp` es un directorio, copia todos los anteriores argumentos ahí.

---

Wildcard (`*`). Buscar cualquier expresión que cumpla con alguna especificación:

```sh
cp *.txt
```

---

Pipes. Usar el *Standard Out* de un programa como el *Standard In* de otro programa.

```sh
ls -1 | wc -l
ls -1 *.txt | wc -l
```

---

Curl. Carga el URL e imprime el contenido como *Standard Out*

```sh
cd ~/linux_test
curl https://www.gutenberg.org/cache/epub/10/pg10.txt
curl https://www.gutenberg.org/cache/epub/10/pg10.txt > The_Bible.txt
sed -r 's/\s+/\n/g' The_Bible.txt | grep lord
sed -r 's/\s+/\n/g' The_Bible.txt | grep -i lord
sed -r 's/\s+/\n/g' The_Bible.txt | grep -i lord | wc -l
sed -r 's/\s+/\n/g' The_Bible.txt | grep -i lord | wc -l > lord_count.txt
curl -s https://www.gutenberg.org/cache/epub/10/pg10.txt | sed -r 's/\s+/\n/g' | grep -i 'lord' | wc -l
```

---

En caso de que el contenido este comprimido (*gzipped*).

```sh
curl -s https://www.gutenberg.org/cache/epub/10/pg10.txt | gunzip | sed -r 's/\s+/\n/g' | grep -iE 'l(adder|ord)' | wc -l > lord-count.txt
```

---

- `sed`. Substituciones (en este caso cambia los espacios en blanco por una nueva linea).
- `grep`. Filtro (en este caso buscar todas las veces que aparece la palabra *lord*). La opción `-i` hace que la búsqueda sea case-insensitive y la opción `-E` para interpretar los patrones `( | )`.
- `wc -l`. Contar el numero de lineas (en este caso todas las lineas dicen alguna variación de *lord*)
