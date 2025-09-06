# spark challenge
Repositorio para challenge de Spark

## Instrucciones:
* Clonar este repositorio desde un IDE (recomendado: PyCharm o Visual Studio)


* Crear un entorno virtual en la carpeta del proyecto, con venv en PyCharm o similar. Necesario python >= 3.10.
  * En PyCharm: File -> Settings... -> Project -> Python interpreter -> Add interpreter -> Add local interpreter. No
  marcar la casilla de "Inherit global site-packages".
  * Abrir una terminal de Windows (o el SO que estemos usando) y activar el entorno virtual creado.
  * Instalar el contenido del fichero requirements con `pip install -r requirements.txt` que incluye pyspark==3.5.0
  * Para que funcione adecuadamente Spark en Windows, es necesario haber seguido las instrucciones del mensaje de 
  bienvenida del foro, donde se explica cómo instalar la JDK, configurar la variable de entorno JAVA_HOME y 
  también HADOOP_HOME tras descargar winutils y la biblioteca DLL de Hadoop para Windows.
  * La propiedad `EXECUTION_ENVIRONMENT` del fichero config.json tendrá valor `"local"`.
  * Por tanto, el objeto `self.spark` de la clase `FlujoDiario` será una SparkSession convencional. 
  * El mismo entorno virtual que has creado te sirve para probar los tests unitarios.
  * Podrás probar también la ingesta ejecutando el notebook en tu ordenador, y la tabla se creará como manejada en el
  catálogo que se creará automáticamente en tu disco duro, en la carpeta desde la que estés haciendo la ejecución
  (carpeta con nombre spark-warehouse o similar). Se recomienda usar solo `database.nombretabla` para la tabla de salida,
  sin catálogo.
    * Es posible que necesites instalar JupyterLab para ejecutar el notebook, ya que algunos IDEs como PyCharm sólo
    permiten ejecutar notebooks en un proyecto en su modalidad Professional.


### Cosas que tener en cuenta

Una vez clonado, las instrucciones se encuentran en [este notebook](notebooks/actividad_spark.ipynb). La idea es
generar un paquete de Python, instalarlo y probar su funcionamiento en el notebook. 


La tabla del catálogo en la que escribiremos el resultado **DEBE SER UNA TABLA MANEJADA** para simplificar la 
configuración, ya que Unity Catalog requiere dar permisos expresamente para poder escribir rutas en tablas externas
(en concreto requiere crear una External Location y darle permisos, algo tedioso). Por tanto, **NO se debe usar la
`option("path", "....")` al escribir**.

Los tests unitarios del fichero `test_ingesta.py` no pertenecen al paquete como tal (y no deben hacerlo). Por lo tanto 
los tests deben entregarse como fichero separados. La entrega serán tres ficheros
separados (¡no deben comprimirse!):
* Fichero wheel creado a partir del proyecto
* Fichero de notebook relleno, con el nombre `actividad_spark.ipynb` (sin cambiarle el nombre al archivo)
* Fichero `test_ingesta.py` relleno, con los tests unitarios.

Los ficheros JSON  que se vayan a utilizar como ficheros de entrada deben ser subidos al contenedor de ADLS 
y su ruta debe estar indicada en las variables `path_json_primer_dia` y `path_json_segundo_dia` del notebook.

