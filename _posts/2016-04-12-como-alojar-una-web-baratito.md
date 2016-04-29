---
layout: post
title:  "Cómo alojar una web baratito"
tags:
- Alojamientos
- Github
- Pages
categories:
- Articulos
- Proyectos
---
Me he animado a escribir este post porque recientemente he mantenido unas conversaciones sobre cuánto cuesta hacer una web y que ha coincidido con la migración de este blog a otro alojamiento. Sirva esta pequeña historia para reflejar que se puede tener una web con dominio propio de manera con un coste mínimo.

Para una pequeña empresa o un particular que quiere tener una web con poco movimiento, simplemente quiere tener un catálogo online de sus productos y servicios, con una transaccionalidad pequeña o nula, posiblemente este artículo le sirva.

Lo primero de todo que tenemos que hacer si queremos ser algo bonito, es tener nuestro propio dominio, hay infinidad de empresas y páginas que te permiten registrar tu domino, en mi caso es un dominio .es, pero puede elegir el que mejor te convenga. Los .es a día de hoy tienen un precio de unos 8.5 €/año. La empresas suelen ofrecerte paquetes de alojamiento, en mi caso lo he rechazado ya que estoy buscando el precio más barato, eso sí, es muy recomendable, imprescindible diría yo, que se permita acceder a la configuración de DNS, ya que de esta manera podremos redirigir el dominio al alojamiento que queramos.

El alojamiento que comentábamos anteriormente lo haremos por ejemplo en github, sí, sí en github. Github tiene un servicio que permite que una rama de un repositorio sea publicada como paginas estáticas, se llama [Github Pages](https://pages.github.com/). Es como los antiguos alojamientos estáticos que ofrecía lycos pero en lugar de utilizar un ftp o un cliente web, lo hacemos con el control de versiones GIT.

Respecto a la programación podemos hacer la típica página o paginas HTML, escribiendo a pelo todo el código o utilizando un generador/asistente WYSIWYG, podemos alojar una página con dinamismo gracias a frameworks como AngulaJS.

En mi caso, utilizo otro servicio que tiene Github Pages que es el soporte a [Jekyll](http://jekyllrb.com/). [Jekyll](http://jekyllrb.com/) es un generador de sitios estáticos, se supone que tu escribes el post en ficheros HTML, Mark Down, etc. y cuando haces push y lo subes a Github lo interpreta y genera las paginas HTML que conformaran el sitio, es muy útil para pequeños blogs o sitios sin tener que saber demasiado HTML y CSS, por defecto te trae una plantilla que no es demasiado bonita pero para gente que no quiere complicarse es suficiente. El único inconveniente que veo, que no puedes programar la publicación de posts, ya que genera la página según hace push, pero da soporte incluso a <a href="/feeds/posts/default" target="_blank" data-proofer-ignore>rss</a> como podéis ver.

Como veis, el único dato económico que os he puesto es el precio del dominio, ya que Github es gratuito y los servicios que ofrecen también, la única condición para no cobrar es que los repositorios sean públicos.

El otro coste es el tiempo que quieras dedicarle a que tu web quede chula y actualizada.

**Enlaces de interés**

- [Dominios .es](http://dominios.es)
- [Github Pages](https://pages.github.com/)
- [Using a custom domain with GitHub Pages](https://help.github.com/articles/using-a-custom-domain-with-github-pages/)
- [Jekyll](http://jekyllrb.com/)
