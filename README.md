<div align="center" style="line-height: 1.15;">
  <img src="Imagen1.png" alt="Logo Universidad Tecnológica del Norte de Guanajuato" width="350"><br><br>
  
  <h2>Universidad Tecnológica del Norte de Guanajuato</h2>
  <p><strong>30 de Mayo 2026</strong></p>
  
  <h3>Automatización de Infraestructura Digital</h3>
  <h4>Instrumento de Evaluación</h4>
  <h4>Unidad I. Entornos de desarrollo en la automatización de redes</h4>
  
  <br>
  <p><strong>Docente:</strong><br>
  Erick Domenzain Morales</p>
  
  <p><strong>Integrantes:</strong><br>
  Héctor Daniel Beltrán Gutiérrez - 1223100387</p>
</div>
 
## Índice
 
1. [Introducción](#introducción)
2. [Desarrollo](#desarrollo)
   - [Descripción de las herramientas de desarrollo](#descripción-de-las-herramientas-de-desarrollo)
   - [Procedimiento de instalación](#procedimiento-de-instalación)
   - [Evidencia de pruebas de verificación de funcionamiento](#evidencia-de-pruebas-de-verificación-de-funcionamiento)
3. [Conclusión](#conclusión)
4. [Anexos: Recursos de la comunidad](#anexos-recursos-de-la-comunidad)
5. [Bibliografía](#bibliografía)

---
 
## Introducción
 
<div align="justify" style="line-height: 1.15;">
El presente reporte detalla de manera exhaustiva el procedimiento de instalación, configuración y validación de las herramientas esenciales para establecer un entorno de desarrollo profesional orientado a la automatización de redes y la gestión de infraestructura digital. En el panorama tecnológico actual, la capacidad de desplegar aplicaciones y servicios de red de forma consistente y reproducible es un pilar fundamental de la ciberseguridad y la administración de sistemas. La automatización elimina el error humano, optimiza los tiempos de entrega y permite mantener políticas de seguridad estrictas en infraestructuras complejas, ya sean servidores locales, entornos virtualizados en Proxmox VE o despliegues en la nube pública.
 
Este documento consta de diversas secciones críticas que abordan desde la concepción teórica de las herramientas hasta su implementación práctica. Inicialmente, se expone una descripción técnica de las tecnologías seleccionadas, incluyendo Docker Engine, Docker Compose y Docker Swagger, destacando su relevancia en la orquestación de contenedores y la documentación de interfaces de programación de aplicaciones (APIs). Posteriormente, se documenta paso a paso la instalación técnica de estos componentes, así como del editor de código Visual Studio Code y el sistema de control de versiones Git, garantizando que el entorno de desarrollo sea robusto y altamente colaborativo.
 
La actividad práctica de esta unidad consistió en el despliegue de una aplicación completa de Sistema de Ventas mediante Docker Compose, integrando cuatro servicios interconectados: una base de datos MySQL, una interfaz de administración PhpMyAdmin, un servidor backend en Node.js y un servidor frontend con Nginx. Este ejercicio no solo solidifica las bases prácticas en la creación de contenedores y microservicios, sino que también prepara el terreno para la orquestación avanzada en unidades posteriores del curso.
</div>

---

## Desarrollo
 
### Descripción de las herramientas de desarrollo
 
<div align="justify" style="line-height: 1.15;">

- **Docker Engine:** Es la tecnología principal subyacente que permite crear y ejecutar contenedores de software de manera aislada. Funciona como un motor cliente-servidor, donde el demonio de Docker gestiona imágenes, contenedores, redes y volúmenes, permitiendo empacar aplicaciones con todas sus dependencias para asegurar que funcionen de manera idéntica en cualquier entorno de hardware o sistema operativo.
- **Docker Compose:** Es una herramienta diseñada para definir y ejecutar aplicaciones Docker de múltiples contenedores. Utiliza un archivo YAML (`.yml`) para configurar los servicios, redes y volúmenes de la aplicación. Con un solo comando (`docker-compose up`), Compose permite inicializar todos los servicios declarados, simplificando drásticamente el despliegue de infraestructuras complejas, como arquitecturas que requieren bases de datos acopladas a servidores web.
- **Docker Swagger (OpenAPI):** Es un conjunto de herramientas de código abierto construido alrededor de la especificación OpenAPI que ayuda a diseñar, construir, documentar y consumir APIs RESTful. Al integrarse y desplegarse mediante Docker, permite a los desarrolladores y administradores de red contar con un entorno local estandarizado para probar puntos finales de red y automatizar la generación de documentación técnica interactiva.

</div>

---
 
### Procedimiento de instalación
 
#### Entorno de virtualización
 
<div align="justify" style="line-height: 1.15;">
Todo el entorno de desarrollo fue configurado sobre una máquina virtual con **Ubuntu Server 22.04 LTS** ejecutada en **Oracle VirtualBox**. Se descargó la imagen ISO oficial de Ubuntu Server desde [https://ubuntu.com/download/server](https://ubuntu.com/download/server) y se creó una máquina virtual con los recursos necesarios (memoria RAM, almacenamiento y adaptador de red en modo puente) para garantizar conectividad con el equipo anfitrión. Esta arquitectura de virtualización permite reproducir el entorno de manera aislada y consistente, simulando un servidor real de producción.
</div>

![Ubuntu 22.04 verificación](ubuntu_22.png)
 
---
 
#### 1. Instalación de Visual Studio Code y Plugins
 
<div align="justify" style="line-height: 1.15;">
Visual Studio Code se instaló en el equipo anfitrión (host) desde el sitio oficial [https://code.visualstudio.com/](https://code.visualstudio.com/). Para trabajar de forma remota sobre la máquina virtual, se utilizó la extensión **Remote - SSH**, que permite editar archivos directamente en el servidor Ubuntu desde el editor local. Adicionalmente se instalaron las siguientes extensiones clave:
 
- **Docker** — Gestión de contenedores e imágenes desde el editor.
- **YAML** — Soporte para sintaxis y validación de archivos `.yml`.
- **GitLens** — Integración avanzada con el historial de Git.
- **Remote - SSH** — Conexión y edición remota sobre la máquina virtual.
</div>

![VSCode con Remote SSH y archivos del proyecto](visual.png)
 
---
 
#### 2. Instalación de Docker en Ubuntu Server 22.04
 
<div align="justify" style="line-height: 1.15;">
La instalación de Docker Engine se realizó directamente en la máquina virtual con Ubuntu Server 22.04 siguiendo el procedimiento oficial para distribuciones basadas en Debian.
</div>

- **Actualizar el índice de paquetes e instalar dependencias:**
```shell
sudo apt-get update
sudo apt-get install -y ca-certificates curl gnupg
