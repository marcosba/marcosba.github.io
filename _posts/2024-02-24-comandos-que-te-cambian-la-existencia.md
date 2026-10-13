---
layout: post
title: "Comandos Que Te Cambian La Existencia"
date: 2024-02-24 13:38:00 -03:00
categories: [IA, Tecnología]
---

En este blog te dejo un arsenal de técnicas para convertirte en un maestro de las búsquedas. Desde encontrar ese video perdido de YouTube hasta descargar música de Spotify, te muestro cómo aprovechar comandos y motores de búsqueda como si fueran un superpoder.

[![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEixcLBZXKPsJecbtn_E_YiN5DFz2wwh8gWDZgmRUxNvvyWIhkkiuFAGp)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEixcLBZXKPsJecbtn_E_YiN5DFz2wwh8gWDZgmRUxNvvyWIhkkiuFAGp)

## Convertite en un ninja del teclado 🥷

### Google Search

#### Videos, películas y series:

```bash
intext:"Search Term" intitle:"index.of" +(wmv|mpg|avi|mp4|mkv|mov) -inurl:(jsp|pl|php|html|aspx|htm|cf|shtml)
```

#### Imágenes:

```bash
intext:"Search Term" intitle:"index.of./" (bmp|gif|jpg|png|psd|tif|tiff) -inurl:(jsp|pl|php|html|aspx|htm|cf|shtml)
```

#### Música:

```bash
intext:"Search Term" intitle:"index.of./" (ac3|flac|m4a|mp3|ogg|wav|wma) -inurl:(jsp|pl|php|html|aspx|htm|cf|shtml)
```

#### Libros:

```bash
intitle:"Search Term" (pdf|epub|mob) "name or title" -inurl:(jsp|pl|php|html|aspx|htm|cf|shtml)
```

---

## Google Drive

```bash
site:drive.google.com
site:drive.google.com +"drive/folders" + term
site:drive.google.com +"spreadsheets" + term
site:drive.google.com +"documents" + term
```

---

## BASH

### Mostrar todos los tipos de archivos en un directorio:

```bash
find . -type f | perl -ne 'print $1 if m/\.([^.\/]+)$/' | sort -u
```

```bash
find . -type f | awk -F. '!a[$NF]++{print $NF}'
```

> Nota: `-F` en `awk` permite separar por un delimitador y `$NF` toma el último campo.

### Contar archivos por directorio:

```bash
find . -type 'f' -printf '%h\n' | sort | uniq -c
```

### Eliminar directorios con solo 1 archivo:

```bash
find . -type 'f' -printf '%h\n' | sort | uniq -c | awk '{ if ($1 == "1") printf "%s%c",$2,0 }' | xargs -0 -I {} rm -rf {}
```

### Evitar mensajes de "Permiso denegado":

```bash
find ./ -iname "term" 2>&1 | grep -v "Permission denied"
```

---

## Web Scraping

### Básico:

```bash
#!/bin/bash
truncate -s 0 plist
counter=1
while [ $counter -le 11 ]
do
  lynx -dump https://howtoarsenio.blogspot.com/2021/$counter/* >> plist
  ((counter++))
done
cat plist | grep -Eo '(http|https)://[^<"]+' | sort -u
```

---

## Búsqueda y organización

```bash
grep "texto a buscar" archivofuente.txt | grep -v -ie "comments" | sort -u > archivo.txt
cat messages*.html | grep -Eo '(http|https)://[^<"]+' | sort -u
cat *.html | grep -H -R 'Goku'
lynx -dump -listonly https://t.me/s/howtoarsenio | grep -o "http:.*" | grep -E -v "http://t.me|http://www.t.me" | sort | uniq > file.txt
```

---

## Listados y Descargas

```bash
ls -1 | sed -e 's/\.png$//'
wget -c -nc -r --no-parent -R "index.html*"
```

> `-c` continua, `-nc` evita sobreescribir, `-r` recursivo y `-R` rechaza extensiones.

---

## Renombrar y Eliminar Archivos

```bash
for i in chr*.fasta; do mv "$i" "${i/%.fasta/.fa}"; done
find ./ -type f -size 0
find ./ -type d -empty -delete
```

---

## FFmpeg

```bash
ffmpeg -i in.avi -c:v libx264 -preset slow -crf 18 -c:a aac -b:a 192k -pix_fmt yuv420p -movflags +faststart out.mp4
```

Y si no hay audio:

```bash
ffmpeg -i in.avi -c:v libx264 -preset slow -crf 18 -pix_fmt yuv420p -movflags +faststart out.mp4
```

---

## ImageMagick

```bash
convert -background transparent "favicon.png" -define icon:auto-resize=16,24,32,48,64,72,96,128,256 "folder.ico"
convert -density 300 -quality 100 in.pdf out.jpg
convert -crop 50%x100% +repage +adjoin img.tif img.tif
```

---

## PowerShell

```powershell
Get-ChildItem | where-object {$_.length -gt 60000000} | Sort-Object length | ft fullname, length -auto
```

---

## Descargar música de Spotify con spotDL

```bash
C:/Windows/System32/bash.exe -c "spotdl --output '/mnt/c/temp' --lyrics-provider genius 'https://open.spotify.com/playlist/7j5tAMUPNuhRFDcP1iClui'"
spotdl "https://open.spotify.com/playlist/7j5tAMUPNuhRFDcP1iClui" --output "C:\temp" --lyrics-provider genius
```

---

## Expresiones Regulares

```bash
<[^>]*>\n
(http|ftp|https)://([\w_-]+(?:(?:\.[\w_-]+)+))([\w.,@?^=%&:/~+#-]*[\w@?^=%&/~+#-])?
```

---

## CMD

```cmd
dir /b /s /a:-D
```

---

## Bonus: videos de YouTube como playlist

Agregá esto al final de la URL:

```text
&feature=mfu_in_order&list=UL
```

Por ejemplo:

```text
https://www.youtube.com/watch?v=D2qO5nMOM5U&feature=mfu_in_order&list=UL
```

Estas son herramientas muy útiles para trabajar con archivos, descargar recursos, extraer datos y automatizar tareas pesadas sin depender de interfaces gráficas.
