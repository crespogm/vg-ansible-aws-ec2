

**¿Qué son los módulos de Ansible?**

Los módulos de Ansible son unidades de código que implementan una tarea específica en un host remoto. Los módulos se pueden utilizar para realizar una amplia gama de tareas, como instalar software, configurar servicios, administrar archivos y directorios, y mucho más.

Los módulos de Ansible son una parte fundamental de la plataforma Ansible. Se utilizan para implementar tareas de automatización de TI de forma consistente y escalable.

**Connection: local**

La opción `connection: local` se utiliza para ejecutar un playbook de Ansible en el nodo de control local. Esta opción es útil para probar un playbook antes de ejecutarlo en hosts remotos.

Por ejemplo, si tenemos un playbook llamado `playbook.yml` que configura un servidor web, podemos ejecutarlo en el nodo de control local con el siguiente comando:

```
ansible-playbook playbook.yml --connection=local
```

Este comando ejecutará todas las tareas del playbook en el nodo de control local.<>

**Detalles del módulo amazon.aws**

El módulo amazon.aws es un módulo de Ansible que proporciona acceso a la API de Amazon Web Services (AWS). El módulo se puede utilizar para realizar una amplia gama de tareas en AWS, como crear instancias, asociar claves de seguridad, crear volúmenes de almacenamiento, y mucho más.

El módulo amazon.aws está disponible en la biblioteca de módulos de Ansible. Para utilizarlo, primero debe instalar el módulo en su control de Ansible. Puede hacerlo utilizando el comando `ansible-galaxy install amazon.aws`.

Una vez que haya instalado el módulo, puede utilizarlo en sus playbooks de Ansible. Por ejemplo, el siguiente playbook utiliza el módulo amazon.aws para crear una instancia EC2:

```yaml
---
- hosts: all
  tasks:
    - name: Create EC2 instance
      aws_instance:
        name: my_instance
        image: ami-01234567890abcdef
        instance_type: t2.micro
        wait: yes
```

Este playbook creará una instancia EC2 con el nombre "my_instance". La instancia se creará a partir de la imagen AMI "ami-01234567890abcdef" y utilizará el tipo de instancia "t2.micro". El playbook también esperará a que la instancia se inicie antes de continuar.



El módulo amazon.aws proporciona una amplia gama de opciones que le permiten personalizar sus solicitudes a la API de AWS. Puede obtener más información sobre las opciones disponibles en la documentación del módulo.

Aquí hay algunos ejemplos de cómo puede utilizar el módulo amazon.aws:

* Crear y administrar instancias EC2
* Crear y administrar volúmenes de almacenamiento
* Crear y administrar claves de seguridad
* Crear y administrar grupos de seguridad
* Crear y administrar instancias de Elastic Beanstalk
* Crear y administrar instancias de Amazon RDS
* Crear y administrar instancias de Amazon S3

El módulo amazon.aws es una herramienta poderosa que puede ayudarlo a automatizar sus tareas de AWS.


* **Amazon Elastic Block Store (EBS)**: EBS proporciona almacenamiento persistente para instancias de Amazon EC2. EBS se puede utilizar para almacenar datos de aplicaciones, sistemas operativos, archivos de registro, etc.
* **Amazon Simple Storage Service (S3)**: S3 proporciona almacenamiento de objetos escalable, duradero y económico. S3 se puede utilizar para almacenar archivos de datos, imágenes, videos, etc.
* **Amazon FSx for Windows File Server:** FSx for Windows File Server proporciona un servicio de almacenamiento de archivos compatible con Windows que se ejecuta en AWS. FSx for Windows File Server se puede utilizar para compartir archivos entre instancias de Amazon EC2, entre usuarios y entre aplicaciones.

**Grupos de seguridad**

* **Grupos de seguridad de instancias:** Los grupos de seguridad de instancias controlan el tráfico entrante y saliente de las instancias de Amazon EC2. Los grupos de seguridad de instancias se pueden utilizar para restringir el acceso a las instancias de Amazon EC2 a solo las direcciones IP o rangos de direcciones IP permitidos.
* **Grupos de seguridad de red:** Los grupos de seguridad de red controlan el tráfico entrante y saliente de las redes virtuales de AWS (VPC). Los grupos de seguridad de red se pueden utilizar para restringir el acceso a las VPC a solo las direcciones IP o rangos de direcciones IP permitidos.

**Elastic Beanstalk**

* **Elastic Beanstalk:** Elastic Beanstalk es un servicio que automatiza el despliegue y la escalabilidad de aplicaciones web y de aplicaciones móviles. Elastic Beanstalk puede utilizarse para implementar aplicaciones en instancias de Amazon EC2, Amazon ECS o Amazon Lambda.

**Amazon RDS**

* **Amazon RDS:** RDS proporciona bases de datos relacionales administradas en AWS. RDS se puede utilizar para implementar bases de datos MySQL, PostgreSQL, MariaDB, Oracle y Microsoft SQL Server.

**Amazon S3**

* **S3:** S3 proporciona almacenamiento de objetos escalable, duradero y económico. S3 se puede utilizar para almacenar archivos de datos, imágenes, videos, etc.

**Ejemplos:**

* **Almacenamiento:**
    * Una aplicación web que almacena datos de usuarios en un bucket de Amazon S3.
    * Una base de datos MySQL que almacena datos en volúmenes de Amazon EBS.
* **Grupos de seguridad:**
    * Un grupo de seguridad de instancias que permite el acceso SSH a una instancia de Amazon EC2 desde una dirección IP específica.
    * Un grupo de seguridad de red que permite el acceso a una VPC desde el Internet público.
* **Elastic Beanstalk:**
    * Una aplicación web que se implementa en instancias de Amazon EC2 utilizando Elastic Beanstalk.
    * Una aplicación móvil que se implementa en Amazon Lambda utilizando Elastic Beanstalk.
* **Amazon RDS:**
    * Una base de datos MySQL que se implementa en Amazon RDS.
    * Una base de datos Oracle que se implementa en Amazon RDS.
* **Amazon S3:**
    * Un sitio web que almacena imágenes en un bucket de Amazon S3.
    * Una aplicación móvil que almacena datos de usuarios en un bucket de Amazon S3.

Estos son solo algunos ejemplos de cómo se pueden utilizar estos servicios de AWS. Hay muchas otras posibilidades, dependiendo de las necesidades específicas de su aplicación o entorno.

```yaml
---
- hosts: all
  tasks:
    - name: Create EFS filesystem
      amazon.aws.efs:
        filesystem_name: my-efs-filesystem
        performance_mode: generalPurpose
        throughput_mode: bursting
        region: us-east-1
    - name: Mount EFS filesystem
      mount:
        path: /mnt/efs
        src: fs-0123456789abcdef0
        state: mounted
```

Este playbook crearía un sistema de archivos EFS llamado `my-efs-filesystem` en la región `us-east-1`. También montaría el sistema de archivos en el directorio `/mnt/efs` en todos los hosts.

**Ejemplo de grupo de seguridad**

```yaml
---
- hosts: all
  tasks:
    - name: Create security group
      amazon.aws.ec2_group:
        name: my-security-group
        region: us-east-1
        rules:
          - proto: tcp
            port: 80
            to_port: 80
            from_port: 80
            security_group_id: sg-0123456789abcdef0
          - proto: tcp
            port: 443
            to_port: 443
            from_port: 443
            security_group_id: sg-0123456789abcdef0
```

Este playbook crearía un grupo de seguridad llamado `my-security-group` en la región `us-east-1`. El grupo de seguridad permitiría el tráfico entrante desde el puerto 80 (HTTP) y el puerto 443 (HTTPS).

**Ejemplo de Elastic Beanstalk**

```yaml
---
- hosts: all
  tasks:
    - name: Create Elastic Beanstalk environment
      amazon.aws.elasticbeanstalk:
        application_name: my-application
        environment_name: my-environment
        region: us-east-1
        platform: docker64
        solution_stack_name: 64bit Amazon Linux 2 v4.0.4 running Docker 19.03.13-ce
        instance_type: t2.micro
        healthcheck_url: /
```

Este playbook crearía un entorno de Elastic Beanstalk llamado `my-environment` en la región `us-east-1`. El entorno ejecutaría una aplicación web en una sola instancia de Amazon EC2 de tipo `t2.micro`.

**Ejemplo de Amazon RDS**

```yaml
---
- hosts: all
  tasks:
    - name: Create RDS instance
      amazon.aws.rds:
        instance_class: db.t2.micro
        engine: mysql
        engine_version: 5.7
        instance_name: my-rds-instance
        allocated_storage: 5
        storage_type: gp2
        region: us-east-1
```

Este playbook crearía una instancia de base de datos MySQL llamada `my-rds-instance` en la región `us-east-1`. La instancia tendría 5 GB de almacenamiento y 2 vCPU.

**Ejemplo de S3**

```yaml
---
- hosts: all
  tasks:
    - name: Create S3 bucket
      amazon.aws.s3:
        bucket: my-bucket
        region: us-east-1
```

Este playbook crearía un bucket de S3 llamado `my-bucket` en la región `us-east-1`.

El siguiente playbook crearía un volumen de EBS llamado `my-ebs-volume` de 10 GB de tamaño:

```yaml
---
- hosts: all
  tasks:
    - name: Create EBS volume
      ec2:
        volume_size: 10
        volume_type: gp2
        snapshot_id: ""
        volume_tags:
          Name: my-ebs-volume
```

Este playbook crearía un volumen de EBS de 10 GB de tamaño con el tipo de almacenamiento `gp2`. El volumen se etiquetaría con el nombre `my-ebs-volume`.

[Image of Volumen de EBS]

Este volumen de EBS se puede utilizar para almacenar datos de aplicaciones, archivos multimedia o copias de seguridad. Se puede asignar a una instancia de Amazon EC2 o se puede utilizar de forma independiente.

**You**: y si quiero realizar un snapshot

**Bard**: Para realizar un snapshot de un volumen EBS, puede utilizar el módulo `amazon.aws.ec2_snapshot`. El siguiente playbook crearía un snapshot de un volumen EBS llamado `my-ebs-volume`:

```yaml
---
- hosts: all
  tasks:
    - name: Create EBS snapshot
      ec2_snapshot:
        volume_id: vol-0123456789abcdef0
        name: my-ebs-snapshot
```

Este playbook crearía un snapshot llamado "my-ebs-snapshot" del volumen EBS con la ID de volumen "vol-0123456789abcdef0".

También puede especificar otras opciones para el snapshot, como la descripción, la región y la fecha de caducidad. Por ejemplo, el siguiente playbook crearía un snapshot llamado "my-ebs-snapshot" del volumen EBS con la ID de volumen "vol-0123456789abcdef0" con la descripción "Snapshot de prueba" en la región us-east-1 y con una fecha de caducidad de 30 días:

```yaml
---
- hosts: all
  tasks:
    - name: Create EBS snapshot
      ec2_snapshot:
        volume_id: vol-0123456789abcdef0
        name: my-ebs-snapshot
       description: Snapshot de prueba
       region: us-east-1
       expiration_date: "2024-02-28T00:00:00Z"
```
Los roles de Ansible son una forma de organizar y reutilizar código en proyectos de automatización. Funcionan como un conjunto de tareas, variables y archivos que se pueden utilizar para automatizar una determinada función o configuración en un sistema.

Los roles de Ansible tienen una estructura de directorios definida que facilita su organización y reutilización. La estructura de directorios de un rol de Ansible es la siguiente:

* **defaults:** contiene variables predeterminadas para el rol.
* **vars:** contiene variables que pueden ser sobrescritas por el usuario.
* **tasks:** contiene tareas que se ejecutan para configurar el sistema.
* **files:** contiene archivos que se copian o modifican en el sistema.
* **templates:** contiene archivos de plantilla que se utilizan para generar archivos en el sistema.
* **handlers:** contiene manejadores que se ejecutan cuando se produce un evento determinado.
* **meta:** contiene información sobre el rol, como sus dependencias y su autor.




Los handlers pueden ser útiles para realizar tareas que deben realizarse después de que se hayan completado todas las tareas en un rol. Por ejemplo, un handler podría reiniciar un servicio, reiniciar un sistema o realizar una copia de seguridad de los archivos.

por ejemplo:

```yaml
handlers:
  - name: Send notification
    mail:
      to: admin@example.com
      subject: Ansible run completed
      body: The Ansible run has completed successfully.
```

Este handler enviará un correo electrónico de notificación después de que se hayan completado todas las tareas en el rol.

Para utilizar un handler en un playbook, debes especificar el nombre del handler en la directiva `handlers`. Por ejemplo, el siguiente playbook ejecutará el handler `Restart Apache` después de que se hayan completado todas las tareas:

```yaml
---
- hosts: all
  handlers:
    - name: Restart Apache
      service:
        name: httpd
        state: restarted
  tasks:
    - name: Install Apache
      yum:
        name: httpd
        state: present
```

**Diferencia entre group vars y hosts vars**

Las variables de grupo (`group_vars`) son variables que se aplican a todos los hosts de un grupo determinado. Las variables de host (`host_vars`) son variables que se aplican a un host específico.

Por ejemplo, si tenemos un grupo de hosts llamado `webservers` y queremos configurar todos los servidores web para que usen la misma versión de PHP, podemos definir una variable de grupo llamada `php_version` en el archivo `group_vars/webservers/main.yml`. La variable `php_version` se aplicará a todos los hosts del grupo `webservers`.

Si queremos configurar un servidor web específico para que use una versión diferente de PHP, podemos definir una variable de host llamada `php_version` en el archivo `host_vars/<host_name>/main.yml`. La variable `php_version` se aplicará solo al host especificado.