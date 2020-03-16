# AREP-Patrones-Arquitecturales

## Respos del front y back

- [Back](https://github.com/cdavidd/AREP-Patrones-Arquitecturales-back)
- [Front](https://github.com/cdavidd/AREP-PATRONES-FRONT)

## Configuraciones

### Base de datos Postgresql

1. Entraremos en nuestra cuenta de AWS y crearemos un nuevo servicio nos dirigimos a la parte de base de datos y escogemos RDS

   ![Imágen 1](img/baseDeDatos/dba-01.JPG)

2. Seleccionamos create database

   ![Imágen 1](img/baseDeDatos/dba-02.JPG)

3. Y seguimos los siguientes pasos

   ![Imágen 1](img/baseDeDatos/dba-03.JPG)

4. Llenamos los campos con la información de `usuario` y `contraseña`

   ![Imágen 1](img/baseDeDatos/dba-04.JPG)
   ![Imágen 1](img/baseDeDatos/dba-05.JPG)
   ![Imágen 1](img/baseDeDatos/dba-06.JPG)

5. Le daremos un `nombre` a nuestra base de datos en este caso _tuto_

   ![Imágen 1](img/baseDeDatos/dba-07.JPG)
   ![Imágen 1](img/baseDeDatos/dba-08.JPG)

6. Una vez terminada la configuración le damos crear
7. Ya creada copiaremos el `link de conexión`, el `puerto`, `nombre` de la base de datos, `usuario` y `contraseña`.

   ![Imágen 1](img/baseDeDatos/dba-09.JPG)

8. Pondremos estos datos en nuestra configuración a la base de datos.

   ![Imágen 1](img/baseDeDatos/dba-10.JPG)

9. Para tener conexión habilitaremos el puerto
   ![Imágen 1](img/baseDeDatos/dba-11.JPG)
   ![Imágen 1](img/baseDeDatos/dba-12.JPG)
   ![Imágen 1](img/baseDeDatos/dba-13.JPG)
   ![Imágen 1](img/baseDeDatos/dba-14.JPG)

### Instancia EC2

1. Entraremos a servicios y escogemos las siguientes opciones para la creación

   ![Imágen 1](img/ec2/ec2-01.JPG)
   ![Imágen 1](img/ec2/ec2-02.JPG)
   ![Imágen 1](img/ec2/ec2-03.JPG)
   ![Imágen 1](img/ec2/ec2-04.JPG)

2. Habilitamos el puerto de entrada 8080 ya que por este correrá nuestro servicio back.

   ![Imágen 1](img/ec2/ec2-05.JPG)

3. Revisamos y creamos la instancia.

   ![Imágen 1](img/ec2/ec2-06.JPG)

4. Crearemos o utilizaremos una llave para la conexión de la maquina

   ![Imágen 1](img/ec2/ec2-07.JPG)

5. Seleccionamos la instancia y le damos conectar y seguimos los pasos de conexión.

   ![Imágen 1](img/ec2/ec2-08.JPG)
   ![Imágen 1](img/ec2/ec2-09.JPG)
   ![Imágen 1](img/ec2/ec2-10.JPG)

6. Una vez conectado instalaremos Java, Maven y git

   **Java**:

   - sudo yum install -y java-1.8.0-openjdk-devel
   - sudo yum remove java-1.7.0-openjdk

   **Maven**:

   - wget https://downloads.apache.org/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
   - cd /opt
   - sudo tar -xvzf /**_path donde descargo_**/apache-maven-3.6.3-bin.tar.gz
   - sudo vi /etc/profile y al final del archivo colocamos
   - export M2_HOME="/opt/apache-maven-3.6.3"
   - export PATH="$PATH:$M2_HOME/bin"
     ![Imágen 1](img/ec2/conf-mvn-profile.JPG)
   - guardamos y salimos
   - . /etc/profile

   **Git**:

   - sudo yum install -y git

7. Revisamos que se hayan instalado

   ![Imágen 1](img/ec2/ec2-11.JPG)

8. Clonamos el repositorio [Back](https://github.com/cdavidd/AREP-Patrones-Arquitecturales-back)

   ![Imágen 1](img/ec2/ec2-12.JPG)

9. Entramos al folder del repositorio y ejecutaremos `mvn package` y `mvn spring-boot:run` para correr nuestro servicio
   ![Imágen 1](img/ec2/ec2-13.JPG)

### Bucket S3

1. Clonaremos el repositorio [Front](https://github.com/cdavidd/AREP-PATRONES-FRONT) y modificaremos el siguiente archivo _static/js/apiItem.js_ donde pondremos el dns:8080/ítems de la ec2

   ![Imágen 1](img/s3/s3-01.JPG)

2. Ahora crearemos un Bucket s3

   ![Imágen 1](img/s3/s3-02.JPG)

3. Le daremos en Empezar o Create Bucket

   ![Imágen 1](img/s3/s3-03.JPG)

4. Asignamos un nombre a nuestro servicio

   ![Imágen 1](img/s3/s3-04.JPG)

5. Permitimos el acceso público y creamos

   ![Imágen 1](img/s3/s3-05.JPG)

6. Ingresamos a nuestro Bucket y seleccioamos cargar

   ![Imágen 1](img/s3/s3-06.JPG)

7. Arrastamos el contenido de la carpeta static
   ![Imágen 1](img/s3/s3-07.JPG)
   ![Imágen 1](img/s3/s3-08.JPG)

8. Le damos permisos publicos al contenido

   ![Imágen 1](img/s3/s3-09.JPG)

9. Ingresamos al archivo Index.html y copiamos el URL
   ![Imágen 1](img/s3/s3-10.JPG)
   ![Imágen 1](img/s3/s3-11.JPG)
10. Ingresamos y verificamos que estemos por http y no por https
    ![Imágen 1](img/s3/s3-12.JPG)

11. Llenamos los espacios y tratamos de insertar un ítem  
    ![Imágen 1](img/s3/s3-13.JPG)

12. Para comprobar que se insertó nos dirigimos al dns de la EC2 /items o nos conectamos a la base de datos para rectificar.
