---
layout: post
title:  "Eliminar el archivo index.php en CodeIgniter"
date:   2018-02-23 22:43:00 +0700
categories: [Codeigniter]
---

De forma predeterminada, CodeIgniter incluirá el archivo index.php en las URL:

```
ejemplo.cl/index.php/articulos/editar/10
```
Para quitar el index.php de las URL debemos tener un archivo **.htaccess** en la raíz del proyecto con la siguiente configuración:

```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ index.php/$1 [L]
```
###### Nota: Si tenemos CodeIgniter instalado en un subdirectorio del servidor la regla "RewriteRule" puede variar.
```
RewriteRule ^(.*)$ /subdirectorio/index.php/$1 [L]
```

Ahora sólo queda quitar index.php en la configuración, esto lo hacemos desde el archivo **/application/config/config.php** dejando la variable de configuración "index_page" con un String vacío:

```
$config['index_page'] = '';
```

Y listo.

###### Nota: Estas reglas específicas pueden no funcionar para todas las configuraciones de servidor.
