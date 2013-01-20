ProfileRTVC
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




