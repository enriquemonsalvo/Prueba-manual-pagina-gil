# Manual de Editor página web GIL

![Banner GIL Negro](/GIL%20BANNER%20NEGRO.png)


Este manual está diseñado para facilitar el proceso de edición y mantenimiento de un sitio web WordPress y una página estática en un entorno de desarrollo local utilizando el plugin Simply Static. Este manual está destinado a ser utilizado en un entorno basado en Linux.

Antes de realizar cualquier cambio en WordPress, es fundamental realizar copias de seguridad tanto del sitio web como de la base de datos.

## I. Hacer Respaldo de WordPress:

Para realizar cambios en el sitio web, es necesario acceder a la terminal con permisos adecuados. Para ello, siga estos pasos:

1. Abra una terminal y ejecute el siguiente comando para acceder como superusuario:

```
sudo su
```

2. Navegue al directorio '/var/' utilizando el comando 'cd':

```
cd "/var/"
```

3. Verifique el contenido del directorio con el comando 'ls -lah':

```
ls -lah
```

4. Cree el archivo tar:

```
tar -cvf /ruta/del/archivo/wp_modFECHA.tar.gz www
```

## II. Hacer Respaldo de Base de Datos:

```
mysqldump -uUSUARIO_BASEDEDATOS -p BASEDEDATOS > nombredelacopiadeseguridad.sql
```

Ingrese la contraseña cuando se solicite.
Para esta versión tanto la contraseña como el usuario es UNAM_GILL

```
UNAM_GILL
```

## III. Crear Página Estática

Una vez realizados los cambios y respaldados, utilice el plugin Simply Static en el editor de WordPress en localhost para generar una página estática. Puede seguir el siguiente tutorial: [Convert WordPress Websites into Static Sites with Simply Static](https://www.youtube.com/watch?v=a4xG14NsQUI)

[![Simply Static](yt-simplystatic-image.jpg)](https://www.youtube.com/watch?v=a4xG14NsQUI)

1. Descomprima el archivo zip de Simply Static y déle el formato adecuado ss_modFECHA.tar.gz.

2. En una terminal secundaria, cree una carpeta 'www' en el mismo directorio de Simply Static y dentro de ella cree una carpeta 'html':

```
mkdir www/html
```

3. Mueva todos los archivos generados por Simply Static a la carpeta 'html' y luego mueva la carpeta 'html' a la carpeta 'www':

```
mv www/* www/html/
mv www/html www/
```

4. Asegúrese de que todos los archivos estén dentro de la carpeta 'www'.

## IV. Montar Página Web Estática

1. Elimine la carpeta 'www' para evitar mezclar carpetas:

```
rm -r www
```

2. Copie el archivo tar.gz generado anteriormente en el paso de creación de la página estática al directorio actual:

```
cp ruta/del/archivo/ss_modFECHA.tar.gz .
```

3. Verifique la presencia del archivo utilizando 'ls -lah' y luego descomprima el archivo:

```
tar -xvf ss_modFECHA.tar.gz
```

4. Elimine el archivo tar.gz después de restaurar la página estática:

```
rm -r ss_modFECHA.tar.gz
```

## V. Verificación y Restauración

Después de montar la página estática, verifique su funcionamiento en localhost. En esta versión, no se tiene acceso al editor de WordPress. Si es necesario realizar cambios, debe restaurar la versión anterior de WordPress.

1. Restaurar Versión Anterior:

    Para restaurar una versión anterior de WordPress, siga estos pasos:

   Ubique el archivo tar.gz correspondiente a la versión que desea restaurar (por ejemplo, 'wp_modFECHA.tar.gz').

   Borre la carpeta 'www' actual:

    ```
    rm -r www
    ```

2. Copie el archivo tar.gz al directorio actual y verifique su presencia:

    ```
    cp ruta/del/archivo/wp_modFECHA.tar.gz .
    ls -lah
    ```

3. Descomprima el archivo tar.gz:

    ```
    tar -xvf wp_modFECHA.tar.gz
    ```

4. Asegúrese de que los permisos sean correctos:

    ```
    chown -R www-data:www-data www
    ```

### Notas

Formato para archivos tar:
  - Para WordPress: 'wp_modFECHA.tar.gz'
  - Para Estática: 'ss_modFECHA.tar.gz'
  - Para bases de datos de WordPress: 'wp_db_modFECHA.sql'
  
- Para cada entrega, asegúrese de tener los tres archivos necesarios.

En caso de que Wordpress solicite la contraseña FTP al entrar al editor de Wordpress, sigue los siguientes pasos:

```
sudo su
cd "/var/"
chown -R www-data:www-data www
```

