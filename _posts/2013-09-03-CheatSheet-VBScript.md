---
layout: post
title: CheatSheet VBScript
tags:
- VBScript
categories:
- Cheat Sheets
---
Minitutorial para poder realizar archivos de comandos en Visual Basic Script (.vbs). Personalmente me parece mucho más potentes que los .bat

Suponemos que conocemos la sintaxis básica de vbs.

<h3>Creación</h3>
Vete a windows y crea un nuevo fichero vacio con las extensión .vbs.
¡Ya esta!

<h3>Ejemplos de código</h3>
<h4>Mensajes de aviso</h4>
El básico "Hola Mundo"
<pre>WScript.Echo "Hola Mundo!!"</pre>

Y el mismo con concatenación de cadenas:
<pre>WScript.Echo "Hola mundo!!" &amp; " Firmado. Smurf Dad"</pre>

Esto mismo se puede hacer con la funcion MsgBox
<pre>MsgBox("Hola Mundo!!!)</pre>

Solicitar datos al usuario:

<pre>Input = InputBox("Introduzca algo", "&lt;aquí debe escribir algo&gt;")</pre>

<h4>Manejo de ficheros</h4>
<h5>Escritura de ficheros de texto</h5>
<pre>
    Set fso = CreateObject("Scripting.FileSystemObject")
    Dim outputFile
    outputFile = "./output.txt"
    Set txtStreamOut = fso.OpenTextFile(OutputFile, 2, True)
    WScript.Echo "Escribiendo fichero de salida."
    For i = 1 To 10
    &nbsp; &nbsp; txtStreamOut.writeline "Loop number: " &amp; i
    &nbsp; &nbsp; txtStreamOut.writeline text
    Next
</pre>

<h4>Envío de correo electrónico</h4>

Desde VBScript tenemos la posibilidad de enviar correos electronicos a traves de servidores que pueden ser externos o internos a la maquina en la que estamos ejecutando el script.

A continuación vamos a describir el código necesario para ese envio.

Creamos el objeto de mensaje de correo electrónico.
<pre>Set obj_Email = CreateObject("CDO.Message")</pre>

Incluimos los datos del mensaje. El remitente, el destinatario, el asunto, el propio mensaje, etc, etc.

Hay que apuntar que las direcciones de correo deben ir en formato <i>Nombre a visualizar &lt;direccion_de_email@direccion.com&gt;</i>

<pre>
obj_Email.From = "&lt;dirección del remitente&gt;"
obj_Email.To = "dirección del destinatario"
obj_Email.Subject = "&lt;asunto&gt;"
obj_Email.Textbody = "&lt;cuerpo del mensaje en formato texto&gt;"
obj_Email.HTMLbody = "&lt;cuerpo del mensaje en formato html&gt;"</pre>
El cuerpo en formato texto y en formato HTML son complementarios y se puede informar solo uno de los dos campos o los dos

A continuación configuramos el servidor de envío de correo<br />
<br />
Especificamos que el servidor SMTP no está en el propio equipo desde el que se envía el correo <br />
<br />
<dl class="dl-horizontal">
<dt>Valor &quot;1&quot;</dt>
<dd>Significa que usaremos el servidor SMTP del propio equipo</dd>
<dt>Valor &quot;2&quot;</dt>
<dd>Significa que utilizaremos uno externo</dd>
</dl>
<br />
<pre>
obj_Email.Configuration.Fields.Item("http://schemas.microsoft.com/cdo/configuration/sendusing") = &lt;valor seleccionado&gt;</pre><br />
Especificamos la URL o la IP del servidor SMTP<br />
<pre>
obj_Email.Configuration.Fields.Item("http://schemas.microsoft.com/cdo/configuration/smtpserver") = "smtp.servidor.com"</pre><br />
Especificamos el puerto por el que está escuchando el servidor (En SMTP por defecto suele ser el 25)<br />
<pre>
obj_Email.Configuration.Fields.Item("http://schemas.microsoft.com/cdo/configuration/smtpserverport") = 25</pre><br />
Especificamos el tipo de autenticación que requiere el servidor: <br />
<dl class="dl-horizontal">
<dt>0</dt><dd>Sin autenticación</dd>
<dt>1</dt><dd>Con autenticación básica (texto plano)</dd>
<dt>2</dt><dd>Con autenticación NTLM.</dd>
</dl>
<br />
<pre>
obj_Email.Configuration.Fields.Item("http://schemas.microsoft.com/cdo/configuration/smtpauthenticate") = 1</pre><br />
Especificamos si se usará SSL para el envío<br />
<pre>
obj_Email.Configuration.Fields.Item("http://schemas.microsoft.com/cdo/configuration/smtpusessl") = False</pre><br />
Especificamos el nombre del usuario y la contraseña para autenticarnos en el servidor en el servidor SMTP<br />
<pre>
obj_Email.Configuration.Fields.Item("http://schemas.microsoft.com/cdo/configuration/sendusername") = "&lt;nombre de usuario&gt;"
obj_Email.Configuration.Fields.Item("http://schemas.microsoft.com/cdo/configuration/sendpassword") = "&lt;contraseña de usuario&gt;"</pre><br />
Antes de enviar sólo nos resta actualizar la configuración del objeto mensaje <i>CDO.Message</i><br />
<pre>
obj_Email.Configuration.Fields.Update</pre><br />
Y por último y para finalizar enviamos el mensaje y limpiamos el objeto.<br />
<pre>
obj_Email.Send
Set obj_Email = Nothing</pre><br />
<h4>
Objeto Dictionary</h4>
<h5>
Creación del Objeto</h5>
<br />
<pre>
Set objeto = CreateObject("Scripting.Dictionary")</pre><br />
Para que el objeto no sea sensible a mayúsculas con las claves inmediatamente después de crearlo debemos poner<br />
<pre>
objeto.CompareMode = 1</pre><br />
<h5>
Incluir valores</h5>
<pre>
objecto.add "clave", valor
objeto.item("clave") = valor</pre>
<br />
<h5>
Accediendo a la información</h5>
<pre>
wscript.echo objecto.item("clave")</pre><br />
<h5>
Comprobando la existencia</h5>
<pre>
if objecto.exists("clave") then
&nbsp; &nbsp; 'Existe
else
&nbsp; &nbsp; 'No existe
end if</pre><br />
<h5>
Calcular el número de entradas en el diccionario.</h5>
<pre>
claves = objecto.Keys
entradas = objecto.Items
for i=0 to objecto.Count - 1
&nbsp; &nbsp; 'Ejemplo 1
&nbsp; &nbsp; wscript.echo claves(i) &amp; "=" &amp; entradas(i)
&nbsp; &nbsp; 'Ejemplo 2
&nbsp; &nbsp; wscript.echo claves(i) &amp; "=" &amp; objecto.item(claves(i))
next</pre><br />
<h5>
Borrado de Entradas</h5>
Borrar una entrada en concreto<br />
<pre>
objeto.Remove("clave")</pre><br />
Borrar todas las entradas<br />
<pre>
objecto.RemoveAll</pre><br />
<h4>
Ejecución de procesos</h4>
Ejemplo de código para detectar que se esta ejecutando un proceso determinado en una maquina.<br />
<pre>
Const NOMBRE_PROCESO = "notepad.exe"
Const MAQUINA = "." ' "." indica que en la maquina local
Set oWmi = GetObject("winmgmts:" &amp; {impersonationLevel=impersionate}!\\ &amp; MAQUINA &amp; "\root\cimv2")
Set listaProcesos = oWmi.ExecQuey("Select * from Win32_Process where Name = '" &amp; NOMBRE_PROCESO &amp; "'")
if listaProcesos.Count = 0 then
&nbsp; &nbsp; 'El proceso no existe en ejecucion
else
&nbsp; &nbsp; 'El proceso existe en ejecucion
end if</pre><br />
<h5>
Ejecutar una aplicación</h5>
<pre>
Set oShell = CreateObject("WScript.Shell")<br />
oShell.Run "c:\WINDOWS\notepad.exe", 1, False</pre>