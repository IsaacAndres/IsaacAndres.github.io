---
layout: post
title:  "Configurar host virtuales con XAMPP en Windows"
date:   2018-02-16 13:40:00 +0700
categories: [XAMPP,VirtualHost]
---

1.- Configurar las solicitudes a la dirección del proyecto sean resueltas en el servidor local.

* Debemos editar el archivo host de Windows para mapear el host name y la IP local, este archivo lo encontraremos en la siguiente ruta:

```
C:\Windows\System32\drivers\etc\
```

* En el podremos agregar todas las direcciones de proyectos que necesitemos, lo importante es colocar un host name que no exista. (Evitar los .com, .org, .tv, etc. Por lo general yo uso .local)

Ejemplo:
```
127.0.0.1           nombre-del-proyecto.local
```
2.- Configuara Apache de XAMPP para que resuelva las solicutudes al host name que agregamos.

*  Editamos el archivo httpd-vhosts.conf que si instalamos XAMPP en la ruta por defecto lo encontraremos en:

```
C:\xampp\apache\conf\extra
```

La configuarción para que funcione el host virtual debería ser solo lo siguiente:
```
<VirtualHost *:80>
    ServerName nombre-del-proyecto.local
    DocumentRoot "C:/xampp/htdocs/nombre-del-proyecto/public"
    <Directory  "C:/xampp/htdocs/nombre-del-proyecto/public">
        AllowOverride All
        Require all granted
    </Directory>    
</VirtualHost>
```

Ya  con esto debería estar funcionando el host virtual, solo queda probarlo desde el navegador.

###### Nota: La ruta /public es opcional, esta depende de donde se encuentre el index del proyecto.
