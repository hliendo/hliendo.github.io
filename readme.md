# Mis notas sobre Docker.
# Instalando [nginx-proxy](<https://hub.docker.com/r/jwilder/nginx-proxy/dockerfile>) y [letsencrypt](<https://letsencrypt.org>)

## ¿Que es [nginx](<https://www.nginx.com>)?

Nginx, pronunciado como “***engine-ex***”, es un servidor web de código abierto que, desde su éxito inicial como servidor web, ahora también es usado como proxy inverso, cache de HTTP, y balanceador de carga.

*Algunas compañías de alto perfil que utilizan Nginx incluyen Autodesk, Atlassian, Intuit, T-Mobile, GitLab, DuckDuckGo, Microsoft, IBM, Google, Adobe, Salesforce, VMWare, Xerox, LinkedIn, Cisco, Facebook, Target, Citrix Systems, Twitter, Apple , Intel, y muchos más (fuente).*

*Nginx creado originalmente por* **[Igor Sysoev](https://en.wikipedia.org/wiki/Igor_Sysoev)** *, y tuvo su primer lanzamiento público en octubre de 2004. Igor concibió inicialmente el software como una respuesta al problema C10K, que se refiere al problema de rendimiento de manejar 10,000 conexiones concurrentes.*


Si bien Apache es la opción general más popular, Nginx es, en realidad, el servidor web más popular entre los sitios web con mucho tráfico.

Cuando se analizan las tasas de uso por tráfico, Nginx impulsa el:

* 60.9% de los 100,000 sitios más populares (en comparación con 56.1% en 2018)
* 67.1% de los 10,000 sitios más populares (en comparación con 63.2% en 2018)
* 62.1% de los 1,000 sitios más populares (un 57% en 2018)

De hecho, Nginx se usan los sitios con los usos más intensivos de recursos que existen, incluyendo Netflix, NASA, e incluso WordPress.com.

El uso de Apache, por otro lado, se mueve en la dirección opuesta a medida que aumente el tráfico web del sitio. Apache impulsa el:

* 24.0% de los 100,000 sitios más populares (en comparación con 27.1% en 2018)
* 18.8% de los 10,000 sitios más populares (en comparación con 21.5% en 2018)
* 16.6% de los 1,000 sitios más populares (en comparación con 16.2% en 2018)

Si vemos los términos buscados en Google Search desde 2004 podemos ver que Apache ha estado disminuyendo de forma constante, mientras que Nginx ha experimentado un ligero crecimiento.

Una vez más, cuando se considera que Nginx tiene un mejor rendimiento bajo escala, no es sorprendente que los sitios web con mucho tráfico opten por usar Nginx en lugar de Apache. Echa un vistazo a nuestra comparación más profunda de [Nginx vs Apache](https://kinsta.com/es/blog/nginx-vs-apache/).



##¿Que es [nginx-proxy](<https://hub.docker.com/r/jwilder/nginx-proxy/dockerfile>)?

Nginx-Proxy es una implementación de la aplicación **[docker-gen](https://github.com/jwilder/docker-gen)** en conjunto con [nginx](<https://www.nginx.com>).

Como funciona docker-gen:

**Docker-gen**


# docker-gen

**[docker-gen](https://github.com/jwilder/docker-gen)** es una pequeña aplicación que usa la API (Application Program Interface) y expone los metadatos de un container a plantillas (templates).
Estas plantillas o Templates son provistas a un comando de notificación que es ejecutado para reiniciar el servicio.

Usando **[docker-gen](https://github.com/jwilder/docker-gen)**, se pueden generar automáticamente y recargar los archivos de configuración de Nginx. El mismo enfoque se puede utilizar para el manejo de logs de Docker.

Es un proxy reverso que junto con   **[docker-gen](https://github.com/jwilder/docker-gen)** genera configuraciones basadas en plantillas o templates y fuerza la recarga de nginx.

![nginx-proxy](https://lab.dataannie.com/fochoa/docker-letsencrypt-nginx-proxy-companion/raw/v1.8.1/schema.png)

nginx-proxy puede implementarse de dos maneras, una en un solo container, esto seria con la imagen de nginx-proxy, y otra con dos containers, uno con nginx y otro con docker-gen. 
La implementación con dos contenedores se considera mas avanzada, ya que tendriamos un container con docker-gen, el cual podríamos usar no solo para implementar un proxy reverso, sino también para las otras plantillas que propone docker-gen, como por ejemplo Log Rotation.


Se usaran las imagenes de : 
* **[nginx-proxy](<https://hub.docker.com/r/jwilder/nginx-proxy/dockerfile>)**
* **[letsencrypt-nginx-proxy-companion](<https://hub.docker.com/r/jrcs/letsencrypt-nginx-proxy-companion/>)**



Referencias:
* [¿Que es NGINX y como funciona?](https://kinsta.com/es/base-de-conocimiento/que-es-nginx/)
* [GitHub Nginx-Proxy](https://github.com/nginx-proxy/nginx-proxy)
* [GitHub Docker-Gen](https://github.com/jwilder/docker-gen)
* [Automated Nginx Reverse Proxy for Docker](http://jasonwilder.com/blog/2014/03/25/automated-nginx-reverse-proxy-for-docker/)
* [Jason Wilder Blog](http://jasonwilder.com)
* [Letscrypt Docker Companion en Docker Hub](https://hub.docker.com/r/jrcs/letsencrypt-nginx-proxy-companion)
* [GitHub Letscrypt Docker Companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion)
* [Wiki Letscrypt Docker Companion](https://github.com/JrCs/docker-letsencrypt-nginx-proxy-companion/wiki/Docker-Compose)