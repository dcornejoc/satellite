Automatizacion de Ansible: Health Check de Red Hat Satellite
======================================

## Descripcion del caso de uso

Los objetivos de los playbooks contenidos en este repositorio son:
1. Realizar un cheque del estado de salud de la plataforma
2. Enviar por correo los datos obtenidos producto de la ejecución de la automatización 

## Resumen de pasos automatizados

1. Obtención de datos relevantes de la plataforma
2. Envío de datos mediante correo electrónico en formato PDF

## Requisitos y Consideraciones Importantes

Para la ejecución correcta de los Playbooks creados es necesario contar con lo siguiente:

 - Este rol requiere Ansible 2.2 o superior.
 - Execution Environment ee-unix-asciidoc que incluye el cliente de (oc), ascii-doctor y jq para la generacion del documento.
 - Permisos de Red desde servidor Ansible hacia servidores para comunicación SSH.
 - Usuario con permisos correspondientes de conexión al Sistema Operativo.
 - Credencial de Satellite.
 - Credencial de tipo Máquina creada en Ansible Automation Platform con el usuario de Sistema Operativo. 

## Variables 

*Variables Globales*:
Los valores de las siguientes variables estan presentados en el archivo vars/rhs_vars.yml de la raíz del Proyecto. A continuación la definición de las variables:

- rh_staff: {name: "Fernando Valenzuela", role: "Consultant", email: "fvalenzu@redhat.com" }
  Variables para especificar los datos de los consultores de Red Hat responsables del Proyecto
- customer_staff: {name: "Xavier Cajas", role: "Arquitecto UNIX", email: "xavcjas@pichincha.com" }
  Variables para especificar los datos de los responsables del Proyecto de Banco Pichincha
- rhs_version
  Version de Satellite usada 
- rhs_customer_subject
  Asunto de la tarea, ejemplo: Health Check Satellite
- rhs_customer
  Nombre del Cliente
- ocp_document_version
  Version del documento a generarse
- fecha_ejecucion
  Fecha de ejecución solo incluyendo dia, hora y minuto
- fecha
  Fecha incluyendo solo dia, mes y año
- problemas_servidor_encontrados
  Inicialización de variables para evaluar problemas
- problemas_capsulas_encontrados
  Inicialización de variables para evaluar problemas
- umbral_limite
  Definición de umbral para alertas
- send_email
  Variable para definir si se enviará mail o no
- smtp_host
  IP del servidor SMTP
- smtp_port
  Puerto del servidor SMTP
- mail_from
  Origen del mail
- mail_to
  Destino del mail
- mail_subject 
  Asunto del mail

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
