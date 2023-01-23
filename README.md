# odoo
Servicio Odoo con conexión a PostgreSQL

# 1. Docker-compose
+ Para generar el docker-compose correcto, debemos ir a DockerHub, buscar la imagen oficial de Odoo, y copiar el código del compose, la versión más simple nos serviría.
+ En el servicio de odoo, es importante asegurarse de tiene el parámetro _depends on:_ y el nombre del servicio de la base de datos.
+ En el servicio de la base de datos, debemos añadir a mayores el puerto en el que va a funcionar postgres, este sería: 5432. En caso de que en el ordenador local este puerto estuviese ocupado, se podría solucionar ejecutando el comando _"service postgres stop"_ en la PowerShell.
+ En la base de datos, la parte del enviroment recoge los credenciales con los cuales vamos a acceder a la base, nombre de la base, nombre de un usuario y contraseña para ese usuario. Para este servicio se puede utilizar la imagen de postgres que aparece en DockerHub.
+ Todavía en el servicio de la base de datos, vamos a mapear los datos de la base de datos a una carpeta local, esto lo vamos a hacer mediante el uso de un volumen, y la ruta a los datos de postgres es: _/var/lib/postgresql/data_.

  Al final nos quedaría un fichero asi:

  ![image](https://user-images.githubusercontent.com/91198492/214037057-b06a022e-85a0-49e6-9bda-f40e9ecb5842.png)
  
+ Finalmente lanzaríamos el docker-compose.yml con el comando _docker-compose up_, y en caso de querer tirarlo para realizar alguna modificación: _docker-compose down -v_, "-v" se pone para que elimine todos los volúmenes que hubiese creado.

# 2. PyCharm
Una vez tenemos levantado el contenedor, podemos abrir la carpeta donde se encuentra el Odoo con PyCharm, y enlazar el programa con Docker y con la base de datos.
## Enlazar con Docker
Enlazar con PyCharm con Docker es tan sencillo como ir a la pestaña _Services_ de la barra inferior de la pantalla, pinchar en el "+" y darle a _Docker Connection_, en caso de tener un Docker funcional en el equipo darle a OK, y listo.

![image](https://user-images.githubusercontent.com/91198492/214038864-b3633235-5477-4ff7-be96-9efa80f6cc8c.png)

## Enlazar con PostgreSQL
Enlazar PyCharm con una base de datos también es bastante sencillo, en este caso iremos al panel lateral derecho y seleccionaremos la pestaña de _Database_, pinchamos sobre el "+" > _Data Source_, y seleccionamos el tipo de nuestra base de datos, se nos va a abrir una ventana con los campos para las credenciales de esta, y al rellenarlos correctamente ya estaríamos conectados,
Es posible que tengamos que descargar el Driver, pero el propio PyCharm lo hace si no los tienes.

![image](https://user-images.githubusercontent.com/91198492/214039835-f0e31159-952d-45c4-a8ca-d9189ad6657e.png)
