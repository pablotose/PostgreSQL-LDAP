# PostgreSQL-LDAP



**Instalación PostgreSQL 12**

Lo primero que tendremos que hacer es actualizar la lista de paquetes de Ubuntu 
  
  `$ sudo apt update`
  

Una vez actualizado la lista de paquetes , lo que tenemos que hacer es intalar PostgreSQL 12 , para ello introducimos el siguiente comando en la terminal 
  
  `$ sudo apt-get install postgresql-12`
  
Tras instalar PostgreSQL y sus dependencias se crea un nuevo servicio, el          servicio en cuestión es postgresql.service el cual queda inicializado, en          ejecución y habilitado para su inicio automático con cada arranque del            sistema.
  
Podemos comprobar el estado del servicio con el comando 
  
  `$ sudo systemctl status postgresql`
  
![alt text](https://github.com/pablotose/PostgreSQL-LDAP/blob/master/service_postgresql.png)

  
Para conectarnos a la base de datos de postgreSQL , lo que tenemos que hacer     es iniciar sesión como el usuario postgres
  
  `$ sudo -i -u postgres`
  
  ![alt text](https://github.com/pablotose/PostgreSQL-LDAP/blob/master/psql.png)
  
Ahora estaremos en una shell como el "usuario" postgres , si lanzamos el         comando psql , estaremos dentro de PostgreSQL como el usuario postgres.
    

**Instalación Open LDAP**

Ahora instalaremos OpenLDAP sobre un Ubuntu Server 20.04 , antes que nada lo que tendremos que hacer será actualizar la lista de paquetes 

  `$ sudo apt update`

Para poder instalar SLAP y otras utilidades de LDAP , tendremos que ejecutar el siguiente comando 

  `$ sudo apt install slapd ldap-utils` 

Durante la instalación , se nos lanzará una pantalla para poder poner la contraseña del usuario Administrador de OpenLDAP.

  ![alt text](https://github.com/pablotose/PostgreSQL-LDAP/blob/master/install_slapd.png)


**-- Configuración de OpenLDAP**

Por defecto durante la instalación de SLAPD , el instalador no no muestra una pantalla donde podamos introducir nuestra configuración del dominio. Por lo que esto vendrá por defecto , si lanzamos el siguiente comando veremos una configuración básica de LDAP.

  `$ slapcat`

  ![alt text](https://github.com/pablotose/PostgreSQL-LDAP/blob/master/slapcat.png)


Para poder poner tu propia información , necesitaremos reconfigurar el paquete SLAPD.

  `$ dpkg-reconfigure slapd`

Cuando lanzamos este comando , se nos mostrará una pantalla en la cual podremos configurar la configuración del servidor LDAP , le daremos a que no y procederemos con la configuración.

 
 ![alt text](https://github.com/pablotose/PostgreSQL-LDAP/blob/master/reconfigure_slapd.png)


  - Agregamos nuestro DNS domain name para construir el base DN de nuestro LDAP directory

  ![alt text](https://github.com/pablotose/PostgreSQL-LDAP/blob/master/dns.png)


  - Añadimos el nombre de nuestra organización.
  
    ![alt text](https://github.com/pablotose/PostgreSQL-LDAP/blob/master/organization_name.png)

  
  - Volvemos a asignarle una contraseña al usuario Administrador.
  
  
  - Elegimos mover la base de datos antigua SLAPD y lo removemos.
  
    ![alt text](https://github.com/pablotose/PostgreSQL-LDAP/blob/master/old_database.png)

  
Si ahora volvemos a ejecutar el comando `slapcat` podemos ver que todos los cambios han sido efectuados.

  ![alt text](https://github.com/pablotose/PostgreSQL-LDAP/blob/master/slapcat_2.png)

