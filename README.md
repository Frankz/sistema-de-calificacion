# sistema-de-calificacion

Proyecto de sistema de calificación...

Instalación
===========

1. Crear en el directorio /var/www/ la el directorio para el sistema

sudo mkdir /var/www/sistema-de-calificacion

2. Darle permisos (Debian) correspondientes para poder trabajar sobre el directorio

sudo chown [user]:www-data -R sistema-de-calificacion

3. Dentro de del directorio "/sistema-de-calificacion" crear otro directorio llamado "/public_html"

sudo mkdir /var/www/sistema-de-calificacion/public_html

4. Le damos los siguientes permisos

sudo chmod 2755 -R /var/www/sistema-de-calificacion/public_html

5. Ingresamos al directorio y traemos el repositorio desde github

cd /var/www/sistema-de-calificacion/public_html

git clone https://github.com/Frankz/sistema-de-calificacion.git .

NOTA: Poner como se indica, con el punto "."  al final para que git no cree otro directorio mas dentro de nuestro "/public_html"

6. Dar de alta el sistema en Apache, nos dirigimos al directorio de "sites-available" de apache, y copiamos el archivo de ejemplo "000-default.conf"

cd /etc/apache2/sites-avaialable

sudo cp 000-default.conf sistema-de-calificacion.conf

7. Editar el archivo nuevo archivo creado "sistema-de-calificacion.conf"

sudo nano sistema-de-calificacion.conf

  a. Buscamos la linea "DocumentRoot" y cambiamos "/var/www/html" por la ruta de nuestro
  sistema, "/var/www/sistema-de-calificacion/public_html".
  b. Agregamos debajo dos lineas nuevas:
      ServerName sistema-de-calificacion.local
      ServerAlias www.sistema-de-calificacion.local
  c. Buscamos la linea "ErrorLog ${APACHE_LOG_DIR}/error.log" y la cambiamos por
      "ErrorLog ${APACHE_LOG_DIR}/erro_sistema-de-calificacion.conf"
  d. Buscamos la linea "CustomLog ${APACHE_LOG_DIR}/access_sistema-de-calificacion.conf"

8. Con el archivo editado, damos de alta el sistema:

sudo a2ensite sistema-de-calificacion.con
sudo service apache2 reload

9. Para poder acceder al mismo desde el navegador sera necesario editar el 
    archivo "/etc/hosts"

sudo nano /etc/hosts

  a. La línea "127.0.0.1 localhost" agregarle la dirección de nuestro sistema, quedaría así:
    127.0.0.1 localhost sistema-de-calificacion.local
      
