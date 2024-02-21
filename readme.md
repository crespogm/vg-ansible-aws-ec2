# Ansible for AWS
**AWS access keys introduccion**
Las claves de acceso son credenciales a largo plazo para un usuario de IAM o el Usuario raíz de la cuenta de AWS. Puede utilizar las claves de acceso para firmar solicitudes mediante programación a la AWS CLI o a la API de AWS (directamente o mediante el SDK de AWS). Para obtener más información, consulte Firma de solicitudes API de AWS.

Las claves de acceso se componen de dos partes: un ID de clave de acceso (por ejemplo, AKIAIOSFODNN7EXAMPLE) y una clave de acceso secreta (por ejemplo, wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY). Debe utilizar el ID de clave de acceso y la clave de acceso secreta juntos, como un nombre de usuario y contraseña, para autenticar sus solicitudes.

**AWS access keys configuracion**
En el archivo ansible-vagrant/playbook.yml, modificar las lineas 40 y 47 reemplazando con las access keys que obtenemos de la consola de AWS.

Luego de grabar,

`vagrant up`:


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
