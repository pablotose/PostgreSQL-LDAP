# PostgreSQL-LDAP



**Instalación PostgreSQL 12**

  - Lo primero que tendremos que hacer es actualizar la lista de paquetes de Ubuntu 
  
  > $ sudo apt update
  
  ![alt text](https://github.com/pablotose/PostgreSQL-LDAP/blob/master/hola.png)


  - Una vez actualizado la lista de paquetes , lo que tenemos que hacer es intalar PostgreSQL 12 , para ello introducimos el siguiente comando en la terminal 
  
  > $ sudo apt-get install postgresql-12
  
  - Tras instalar PostgreSQL y sus dependencias se crea un nuevo servicio, el           servicio en cuestión es postgresql.service el cual queda inicializado, en           ejecución y habilitado para su inicio automático con cada arranque del               sistema.
  
  - Podemos comprobar el estado del servicio con el comando 
  
  > $ sudo systemctl status postgresql
  
  
  FOTO DEL SERVICIO ACTIVO.
  
  - Para conectarnos a la base de datos de postgreSQL , lo que tenemos que hacer     es iniciar sesión como el usuario postgres
  
  > $ sudo -i -u postgres
  
  - Ahora estaremos en una shell como el "usuario" postgres , si lanzamos el         comando psql , estaremos dentro de PostgreSQL como el usuario postgres.
    

**Instalación Open LDAP**

- Ahora instalaremos OpenLDAP sobre un Ubuntu Server 20.04 , antes que nada lo que tendremos que hacer será actualizar la lista de paquetes 

> $ sudo apt update

- Para poder instalar SLAP y otras utilidades de LDAP , tendremos que ejecutar el siguiente comando 

> $ sudo apt install slapd ldap-utils 

- Durante la instalación , se nos lanzará una pantalla para poder poner la contraseña del usuario Administrador de OpenLDAP.

FOTO DE LA PANTALLITA

**-- Configuración de OpenLDAP**

