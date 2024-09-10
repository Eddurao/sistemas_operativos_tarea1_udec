
Implementación de una Shell en C para Sistemas Operativos

integrante: Eduardo Parra.
Curso: Sistemas Operativos - Segundo Semestre 2024

1. Introducción
Este documento presenta el desarrollo de una shell programada en C, diseñada para ejecutar comandos de forma 
concurrente. La shell incorpora funcionalidades adicionales como el manejo de tuberías, la gestión de comandos 
favoritos y un sistema de recordatorios. Este proyecto forma parte del curso de Sistemas Operativos y tiene como 
objetivo principal fortalecer las habilidades de los estudiantes en el manejo de procesos en un entorno Unix.

2. Objetivos del Proyecto
El principal objetivo del proyecto es crear una shell con las siguientes capacidades:
- Ejecución de comandos de manera concurrente.
- Implementación de tuberías para la comunicación entre procesos.
- Administración persistente de una lista de comandos favoritos.
- Integración de un sistema de recordatorios temporizados.

3. Funcionalidades Desarrolladas

3.1 Ejecución Concurrente de Comandos
La shell permite al usuario ingresar comandos que se ejecutan en procesos hijos mediante el uso de fork() y execvp(). 
La shell se encarga de esperar la finalización del proceso hijo antes de continuar, lo cual asegura que los comandos se ejecuten en primer plano.

3.2 Soporte para Tuberías
Se ha implementado la capacidad de conectar múltiples comandos a través de tuberías, utilizando pipe() para enlazar la salida de un comando con la entrada de otro. 
Esta funcionalidad permite la ejecución de comandos encadenados, como ps -aux | sort -nr -k 4 | head -20.

3.3 Gestión de Comandos Favoritos
La shell incluye un sistema que permite al usuario almacenar y gestionar sus comandos más utilizados en una lista persistente de favoritos. Las operaciones disponibles incluyen:
- favs crear: Crea un archivo para almacenar comandos favoritos.
- favs mostrar: Muestra la lista actual de comandos favoritos.
- favs eliminar: Permite eliminar comandos de la lista por su identificador.
- favs ejecutar: Ejecuta un comando guardado como favorito.
- favs cargar y favs guardar: Cargan y almacenan la lista de favoritos desde o hacia un archivo.

3.4 Sistema de Recordatorios
La funcionalidad de recordatorios permite al usuario establecer tareas que se activarán tras un tiempo especificado mediante el comando set recordatorio. 
Por ejemplo, set recordatorio 10 'Hacer una pausa activa' mostrará un recordatorio después de 10 segundos, utilizando sleep() en un proceso hijo.

4. Estructura del Código
El código se organiza en funciones clave como ejecutar_comando() para la ejecución de comandos, manejar_pipes() para la gestión de tuberías, y set_recordatorio() para configurar recordatorios, entre otras.

5. Pruebas Realizadas
Las pruebas incluyeron la ejecución de comandos básicos (ls, pwd), la verificación de tuberías (grep, sort), la gestión de favoritos (agregar, eliminar, ejecutar), y la configuración de recordatorios temporizados.

6. Conclusiones
El proyecto logró cumplir con los objetivos planteados, proporcionando una interfaz de shell funcional con características adicionales que mejoran la experiencia del usuario.

7. Repositorio
El código fuente del proyecto está disponible en: https://github.com/Eddurao/sistemas_operativos_tarea1_udec
