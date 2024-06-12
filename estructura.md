# Estándar de estructura de proyectos
Utilice un patrón coherente al estructurar los archivos de su proyecto de Ansible en un sistema de archivos. Hay una serie de patrones útiles que se muestran en la estructura del presente repositorio. 

## Componentes de la estructura
Dentro de la estructura, se puede evidenciar que en la raíz del repositorio se encuentran los archivos “site.yml”, “tomar_snapshot.yml” y “actualizar_os_rhel.yml”, y los directorios “inventories” y “roles”

### Playbook maestro site.yml
El archivo site.yml es el playbook maestro, que importa o incluye los demás playbooks que ejecutan tareas específicas: “tomar_snapshot.yml” y “actualizar_os_rhel.yml”.

### Playbooks de tareas especificas “tomar_snapshot.yml” y “actualizar_os_rhel.yml”
Estos playbooks, como se puede evidenciar en los archivos “tomar_snapshot.yml” y “actualizar_os_rhel.yml”, solo contienen un listado de tareas relacionados a un objetivo especifico, tal como tomar un snapshot en VMware vCenter o actualizar el sistema operativo de una maquina.

### Alojamiento de roles de Ansible
Los roles deben estar en subdirectorios dentro del directorio “roles”, tal como se muestra el rol “std_server”. 

### Alojamiento de inventarios estáticos
También existen dos directorios para alojar inventarios estáticos, los cuales son “inventories/dev/inventory” y “inventories/prod/inventory” para los entornos de desarrollo y producción respectivamente.

Los variables a nivel de grupo y host deben incluirse bajo los subdirectorios “group_vars” y “host_vars” según corresponda.

### Carpeta files
Esta carpeta aloja todos los archivos como scripts y archivos de configuración requeridos para la operación del playbook.

### Carpeta templates
Esta carpeta aloja todos los templates en formato Jinja2 requeridos para la operación del playbook.

### Carpeta utils
Scripts y utilitarios para poder comprobar el codigo y la creacion del archivo de instalacion en produccion.

### Archivo README.md
El archivo README es a menudo el primer elemento que un visitante observa cuando ingrese al repositorio. Los archivos README deben incluir como mínimo la siguiente información:
* Que hace el proyecto.
* Por qué es útil el proyecto.
* Cómo los usuarios pueden comenzar con el proyecto.
* Dónde los usuarios pueden obtener ayuda con su proyecto.
* Quién mantiene y contribuye al proyecto.
