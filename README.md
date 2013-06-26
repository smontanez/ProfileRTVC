1. ProfileRTVC
===========

Prueba Profile RTVC
# Drupal 7 Perfil de instalacion para rtvc radio #

Perfil de instalacion Drupal7 para rtvc radio

## Requerimientos ##

* Una maquina Linux con **Apache**, **MySQL**, **git** y **drush** instalada.
* Crear una base de datos MySQL para Drupal, con un usuario con todos los permisos a esta.

##Pasos para la Instalación drush en Linux:##

Prerrequisitos: 

Ejecutar en el home los siguientes comandos:

pear config-create ${HOME} ${HOME}/.pearrc

pear install -o PEAR

Abrir el .bash_profile y editarlo con vi:

vi .bash_profile

y adicionar las siguientes dos líneas:

export PHP_PEAR_PHP_BIN=/usr/php/53/usr/bin/php

export PATH=${HOME}/pear:/usr/php/53/usr/bin/php:${PATH}

Correr el siguiente comando:

pear channel-discover pear.drush.org

pear install drush/drush


# Instalacion Profile#

Copiar el archivo **build-rtvc.make** a su directorio home

Ejecutar:
 
  drush make build-rtvc.make /var/www/rtvc
  
  cd /var/www/rtvc
  
  drush site-install rtvc --db-url=mysql://<database_user>:<database-user-password>@<database host>/<database name> --account-name=admin --account-pass=pass

2. ProfileRTVC
===========

## Requerimientos ##

* Una maquina Windows con **Apache(version 2.2.23)**, **MySQL(version 5.0.95)**, php(versión 5.3.19) y **git** instalada. Se recomiendan estas versiones dado que son las que actualmente usa el servidor pasarela y producción de RTVC.
* Crear las siguientes bases de datos en MySQL para Drupal:
1. Se crea una BD llamada radiortvc en mysql (para el sitio general)
2. Se crea una BD llamada radionica en mysql (para el sitio radiónica)
3. Se crea una BD llamada radionacional en mysql (para el sitio radionacional)
4. Se crea una BD llamada fonoteca en mysql (para el sitio fonoteca)

* Crear el usuario radioadmin en MySQL con todos los permisos a cada una de las bases de datos y asignarle el password: temporal.
* Descargar en su home el profile comprimido llamado drupal7_profile.tar.gz que se encuentra en este repositorio. Dentro de git ejecutar el comando : git clone https://github.com/rtvc/DrupalProfile.git
* Descomprimir y desempaquetar el .tar.gz anterior.
* Correr los scripts para cada una de las BD que se encuentran en el archivo BDRTVC.tar.gz que se encuentra en este repositorio (el nombre de los scripts corresponden al nombre de las bases de datos dónde se debe ejecutar cada uno de los scripts). 
* Probar en el navegador la instalación. 
* Tener en cuenta que se debe direccionar con DNS o en archivo hosts para que apunte al servidor correspondiente(en el caso de que se este probando en una máquina local debe direccionar cada sitio a localhost). Así mismo se deben modificar los archivos de configuración de apache para hacer un virtual host para que cada sitio apunte a la raíz dónde quedó instalado el profile del drupal que acabo de instalar.
* Los nombres de los sitios son los siguientes: radionica.gov.co, radionacionaldecolombia.gov.co y fonoteca.gov.co
* Se tienen los siguientes password para el usuario: admin en cada uno de los sitios
* Sitio General: v7kZ2Xdi3b
* Sitio radionica: 4vDnC4yjgD
* Sitio radionacional: TBRQz9AQqo
* Sitio fonoteca: DBcdhk5owF

## Notas para montar en otro servidor ##
Para tener en cuenta en el servidor de pruebas si cambian los nombres de dominios y Bases de datos:

*Se debe crear en drupal el archivo sites.php dentro de la carpeta sites con el mismo contenido de example.sites.php, simplemente añadiendo a dónde se va a mapear cada sitio como en el siguiente ejemplo:
$sites['radionica.portalradio.gov.co'] = 'radionica.gov.co';

$sites['radional.portalradio.gov.co'] = 'radionacionaldecolombia.gov.co';

$sites['fonoteca.portalradio.gov.co'] = 'fonoteca.gov.co';

*Si cambian los nombres de las Bases de datos, el usuario y el password de acceso a la BD de cada sitio se debe modificar el settings.php de cada sitio así:

      'database' => 'radionica_portalradio',
      
      'username' => 'pradio',
      
      'password' => 'xxxxxxx'
      
*Tener en cuenta que el servidor tenga:

1. El mod_rewrite habilitado en el apache.

2. El AllowOverride habilitado en el vhost.



