`head`. Imprime un numero determinado de lineas/caracteres de un archivo.
`fold`. Dar formato a texto (*Word-Wrapping* con `-w` y `-s` para no cortar palabras).

```sh
head -n5 The_Bible.txt
head -c10 The_Bible.txt
head -n250 The_Bible.txt | fold -sw 30
```

---

```sh
echo `date +'%F'`.txt
echo Hola >> `date +'%F'.txt`
```

---

`.bashrc`:

```sh
echo Buenas desde `date +%Y`
```

---

Ver los cambios de un archivo (en este caso imprime el tiempo y lo redirige al final del archivo)

```sh
tail -f hola.txt
watch -n5 'echo `date +%c` >> hola.txt'
```

---

*Environment Variables* ($PATH). Son variables definidas por scripts y la Shell.

```sh
export
echo $USER
echo $HOME
var=hola
echo $var
export var
node
process.env.var
```

---

```sh
N=5
echo $((N*5))
echo <hello $USER>
echo '<Hola $USER>'
echo "<Hola $USER>"
echo "<Hola `whoami`b>"
```

---

```sh
export XDG_CONFIG_HOME="$HOME/.config"
export XDG_DATA_HOME="$HOME/.local/share"
export XDG_CACHE_HOME="$HOME/.cache"
```

---

Anadir permisos de ejecutable

```sh
chmod +x script_test.sh
```

---

```sh
#!/usr/bin/evn bash
# To use bash as the non-interactive shell
#!bin/sh
# Using what is inside bin/sh as the non-interactive shell
# ls -l /bin/sh
/bin/sh -> dash*
```

---

`script_test.sh`

```sh
#!/usr/bin/env bash

echo "$(date +'%F.%T') $1" >> "$(date +%F).txt"
# chmod +x script_test.sh
```
