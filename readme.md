# Ansible for AWS
**AWS access keys introduccion**

Las claves de acceso son credenciales a largo plazo para un usuario de IAM o el Usuario raíz de la cuenta de AWS. Puede utilizar las claves de acceso para firmar solicitudes mediante programación a la AWS CLI o a la API de AWS (directamente o mediante el SDK de AWS). Para obtener más información, consulte Firma de solicitudes API de AWS.

En este caso Ansible va a ser quien se conecte de forma programatica para crear y destruir recursos en la AWS Cloud

Las claves de acceso se componen de dos partes: un ID de clave de acceso (por ejemplo, AKIAIOSFODNN7EXAMPLE) y una clave de acceso secreta (por ejemplo, wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY). Debe utilizar el ID de clave de acceso y la clave de acceso secreta juntos, como un nombre de usuario y contraseña, para autenticar sus solicitudes.

AWS access keys configuracion
--------
**En el archivo ansible-vagrant/playbook.yml**

Modificar las lineas 40 y 47 reemplazando con las access keys que obtenemos de la consola de AWS.
```yaml
  - name: Adding the Access Key ID environment variable
    lineinfile: >
      dest=/etc/environment
      state=present
      regexp="^export AWS_ACCESS_KEY_ID"
  --->line="export AWS_ACCESS_KEY_ID=AKIA453Y...."
    become: true
  - name: Adding the Secret Access Key environment variable
    lineinfile: >
      dest=/etc/environment
      state=present
      regexp="^export AWS_SECRET_ACCESS_KEY"
  --->line="export AWS_SECRET_ACCESS_KEY=R5niYqoJh..."
    become: true
```
Asegurarse que luego de la modificacion grabar el archivo.

Establecer un nombre común a los recursos
------------

**En el archivo ansible-aws/group_vars/all.yml**

Modificar la variable "myname", esta variable es la que utiliza el playbook para tagear los recursos y nombrarlos.
```yaml
# Set your unique name
myname:  <----- # CHANGE ME
```
Recursos en AWS utilizando un VM preconfigurada.
-----
**En la terminal**
```
vagrant up
vagrant ssh
cd ansible-aws
ansible-playbook -i inventory playbooks/aws_net_ec2_ngix.yaml
```
Una vez finalizado el plabook podemos ingresar desde un navegador con la ip publica que nos reservó AWS.


**Bugs**
```
The Ansible software could not be found! Please verify
that Ansible is correctly installed on your guest system.

If you haven't installed Ansible yet, please install Ansible
on your Vagrant basebox, or enable the automated setup with the
`install` option of this provisioner. Please check
https://docs.vagrantup.com/v2/provisioning/ansible_local.html
for more information.
```

Corriendo el comando `vagrant provision` Luego de que la maquina virtual sea aprovisionada.
