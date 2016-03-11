---
layout: post
title: Crear apodos a aplicaciones
tags: [Trucos]
---
Existe una característica oculta en el registro de Windows nos permite crear apodos para los programas, por ejemplo, un apodo llamado "bloc.exe" al ser ejecutado inicie otro programa, como por ejemplo el bloc de notas (“notepad.exe”).

<ul>
    <li>Para ello iniciaremos la herramienta de edición del registro de sistema, con el comando <code>regedit.exe</code> desde el menú Inicio/Ejecutar y localizaremos la clave <code>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\App Paths</code>.</li>
    <li>Para crear un nuevo apodo, crearemos una nueva clave, cuyo nombre será el apodo que queremos crear.</li>
    <li>Acto seguido modificaremos el valor <code>(Default)</code> de la clave que contendrá la ruta completa y nombre de la aplicación que será iniciada al ejecutar el alias, en nuestro caso <code>C:\WINDOWS\notepad.exe</code>.</li>
</ul>
Como veis es un truco sencillo que nos puede ayudar en nuestro dia a dia, en mi caso me ha permitido sobre escribir accesos que exisitan para enlazar con aplicaciones que uso habitualmente.