Automatizacion de Ansible: Instalación, Aprovisionamiento y Gestión de Red Hat Satellite
======================================

## Descripcion del caso de uso

Los objetivos de los playbooks contenidos en este repositorio son:
1. Instalar la plataforma Red Hat Satellite
2. Realizar las configuraciones iniciales de la plataforma
3. Gestionar la plataforma post instalación desde Ansible

## Resumen de pasos automatizados

1. Instalar y configurar Satellite - Capsulas: Playbook que permite la instalación de Satellite Server y las cápsulas definidas en la arquitectura. Además, realiza las configuraciones iniciales de ....
2. Gestión de Ubicaciones:
3. Gestión de Manifiestos de Contenido:
4. Gestión de Repositorios de Arquitectura por Defecto:
5. Gestión de Repositorios Individuales:
6. Gestión deRepositorios de Ciclos de Vida de Entornos Completos:
7. Gestión deRepositorios de Ciclos de Vida de Entornos Indivuduales:
8. Gestión de Vistas de Contenido:
9. Publicación o eliminación de versiones de vistas de contenido:
10. Sincronización de repositorios o productos:
11. Gestión de Activation Keys:
12. Suscribir nuevo host:
13. Planes de sincronización:
14. Registrar Lifecycle Environment específico en capsula específica:

## Requisitos y Consideraciones Importantes

Para la ejecución correcta de los Playbooks creados es necesario contar con lo siguiente:

 - Este rol requiere Ansible 2.2 o superior.
 - Execution Environment ee-unix-satellite que incluye los módulos requeridos para ejecutar los comandos específicos para Satellite.
 - Permisos de Red desde servidor Ansible hacia servidores para comunicación SSH.
 - Permisos de Red desde servidor Satellite hacia servidores.
 - Usuario con permisos correspondientes de conexión al Sistema Operativo.
 - Credencial de Satellite.
 - Credencial de tipo Máquina creada en Ansible Automation Platform con el usuario de Sistema Operativo. 

## Variables 

La siguiente variable se ha incluido en el playbook crear_satellite_manifest.yml:

vars:
    satellite_manifest_path: "~/manifest.zip"

Esta variable define la ubicación del manifiesto a usar para cargar en Satellite.

## Pruebas


## Estructura del repositorio

La estructura de archivos de este repositorio es el siguiente:

.
├── azure-pipelines.yml
├── collections
│   └── requirements.yml
├── crear_healthcheck_rh_satellite.yml
├── crear_satellite_activation_keys.yml
├── crear_satellite_locations.yml
├── crear_satellite_manifest.yml
├── crear_satellite_repositories_individual.yml
├── crear_satellite_repositories.yml
├── crear_satellite_sync_plan.yml
├── crear_satellite_users.yml
├── desuscribir_satellite_client.yml
├── estructura.md
├── inputs
│   ├── default-theme.yml
│   ├── fonts
│   │   ├── RedHatDisplay-BlackItalic.ttf
│   │   ├── RedHatDisplay-Black.ttf
│   │   ├── RedHatDisplay-BoldItalic.ttf
│   │   ├── RedHatDisplay-Bold.ttf
│   │   ├── RedHatDisplay-Italic.ttf
│   │   ├── RedHatDisplay-MediumItalic.ttf
│   │   ├── RedHatDisplay-Medium.ttf
│   │   ├── RedHatDisplay-Regular.ttf
│   │   ├── RedHatText-BoldItalic.ttf
│   │   ├── RedHatText-Bold.ttf
│   │   ├── RedHatText-Italic.ttf
│   │   ├── RedHatText-MediumItalic.ttf
│   │   ├── RedHatText-Medium.ttf
│   │   └── RedHatText-Regular.ttf
│   ├── healthcheck_content.adoc
│   ├── images
│   │   ├── Banco_Pichincha_logo.svg.webp
│   │   ├── EngagementJournalCoverPageLogoNew2.png
│   │   ├── EngagementJournalCoverPageLogoNew.jpg
│   │   └── EngagementJournalCoverPageLogoNew.png
│   ├── info_pods.adoc
│   ├── pods_info.adoc
│   ├── prefacio.adoc
│   ├── redhat-theme.yml
│   ├── salidas_filesystem_capsules.html
│   ├── salidas_filesystem_server.html
│   ├── salidas_nodes.adoc
│   ├── salidas_satellite.adoc
│   └── variables.txt
├── instalar_configurar_satellite_capsulas.yml
├── inventories
│   └── aap_prod
│       └── prod_platforms
│           └── inventory
├── prod.json
├── publicar_satellite_content_view_publish.yml
├── README_HC.md
├── README_INSTALL.md
├── registrar_multiples_satellite_lifecycle_environment.yml
├── registrar_satellite_capsule_lifecycle_environment_individual.yml
├── registrar_satellite_content_view.yml
├── registrar_satellite_lifecycle_environment_individual.yml
├── roles
│   ├── satellite-capsule
│   │   ├── defaults
│   │   │   └── main.yml
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── satellite-capsule-configuration
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── satellite-installation-act-keys
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── satellite-installation-cv-cvpublish
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── satellite-installation-manifest
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── satellite-installation-orgs
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── satellite-installation-sync-plans
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── satellite-installlation-repos
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── satellite-lifeceycle-environment
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── satellite-locations
│   │   └── tasks
│   │       └── main.yml
│   └── satellite-server
│       ├── defaults
│       │   └── main.yml
│       ├── handlers
│       │   └── main.yml
│       ├── tasks
│       │   └── main.yml
│       ├── templates
│       │   └── openssl.cnf.j2
│       └── vars
│           └── main.yml
├── sincronizar_satellite_repositories.yml
├── suscribir_satellite_client.yml
├── templates
│   ├── healthcheck_content.adoc.j2
│   ├── prefacio.adoc.j2
│   ├── redhat-theme.yml.j2
│   ├── salidas_filesystem_capsules.html.j2
│   ├── salidas_filesystem_server.html.j2
│   ├── salidas_nodes.adoc.j2
│   ├── salidas_satellite.adoc.j2
│   └── variables.txt.j2
└── vars
    └── rhs_vars.yml

## Importante

Para pasar a producción, el pipeline de pasaje de ambiente instalará dentro de ansible productivo los siguientes elementos:
* Proyecto
* Inventarios
* Job_templates

Todo ello basado en el archivo prod.json en el raiz del repositorio. 

## Código

El código se encuentra disponible en el repositorio.
https://BancoPichinchaEC@dev.azure.com/BancoPichinchaEC/BP-Ansible-Plataformas/_git/ans-aut-arqPlataf-satellite
Dentro del branch: master

## Referencias y documentación relacionada al playbook ⚙️

_Documentación_
* [Documentación oficial modulo ansible](https://docs.ansible.com/ansible/latest/index.html)
