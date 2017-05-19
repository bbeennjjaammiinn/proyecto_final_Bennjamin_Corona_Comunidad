
# Datos genómicos propios obtenidos a través de secuenciación de genomas completos, se procesaran los datos crudos.

# La carpeta Bin contiene los comandos usados para procesamiento de datos crudos y ensamblado del genoma y carpeta Data contiene los archivos con los datos input y ouput de los distintos programas usados.

# Descompresión y primeros vistazos a mis archivos fastqc de genomas de Vibrio

los archivos con los que trabajo se encuentran en formato .tar.gz


# Los dos archivos los descomprimí mediante 

$ tar -xvf miarchivo.tar.gz

# Para ver el tamaño de mis archivos fastq uso

$ ls -lh nombre_del_archivo.fastq

#para ver que aspecto tiene las primeras 15 lineas y ver que realmente estan en formato fastq uso un 

$ head 15 nombredelarchivo

Preprocesamiento de archivos FASTQ con FASTX-Toolkit

Fast_quality_stats

Usare fastx_quality_stats para visualizar las estadísticas de calidad de mis archivos y los comandos usaron seran:

#para obtener la tabla de calidades de los reads

$ fastx_quality_stats -i nombre_de_archivo_de_entrada.fastq -Q33
-o nombre_archivo_de_salida.txt

#para obtener una gráfica de calidades

$ fastq_quality_boxplot_graph.sh -i stats.txt -o plot.png -t prueba_de_calidad

FASTQ Quality Filter y FASTQ Trimer 

Usare FASTQ Quality Filter para filtrar la secuencias en base a su calidad y FASTQ Trimmer para cortar las secuencias en format Fasta o Fastq al remover el ruido y los barcodes los comandos usados seran:

# Eliminar los adaptadores.

$ fastx_trimmer -i archivovibrio.fastq -f 8 -o cortado_archivovibrio.fastq -Q33

#1. eliminar secuencias de menos de 50 nucleótidos(por ejemplo)
$ fastx_clipper -i archivovibrio.fastq -o archivovibrio_m50.fastq -l 50 -Q33 -v

#2. A continuación se recortaran los primeros 15 nucleótidos fijando el tamaño máximo a 500 nt y refiltrando la longitud mínima de 50 (por si al recortar los primeros 10 alguno queda de este tamaño).

$ fastx_trimmer -i archivovibrio_m50.fastq -o archivovibrio_m50_trim10-500.fastq -f 11 -l 500 -m 50 -Q 33 -v

#3.Finalmente se eliminaran los “reads” cuya calidad en el 80% de los nucleótidos no supere un valor phred de 20. En este paso se quitan las secuencias de baja calidad.


$ fastq_quality_filter -i archivovibrio_m50_trim10-500.fastq -o archivovibrio_m50_trim10-500_Qual20.fastq -q 20 -p 80 -Q 33 -v



Ensamblado del genoma con Velvet

Bajar y descomprimir carpeta con el archivo que contiene el programa Velvet 

$cd [directory containing the .tgz file]

$tar xvfz velvet_1.0.17.tgz
$ cd velvet_1.0.17 
#instalar velvet
$ ./make 
Uso del programa Velveth y Velvetg
Primer paso Velveth
# Crear el Roadmap, Velveth une las secuencias pareadas que en un principio estaban separadas en los dos archivos

$ velveth velvet_out 31 -shortPaired -fastq -separate archivovibrioR1.fastq archivovibrio_R2.fastq

# Velvetg genera y usa las gráficas Bruijn, que señala y busca los nodos, que los une para ensamblar y que pueda crear contigs y scaffoldings concatena 
$ velvetg Resularchivovibrio –clean yes –exp_cov 21 –cov_cutoff 2.81 –min_contig_lgth 200
Programa MAUVE para ordenar los scaffolds 
# Bajar y descomprimir carpeta con el archivo que contiene el programa MAUVE y un genoma de referencia para Vibrio

#correr MAUVE y trabajar en un entorno gráfico con java

$java -jar Mauve.jar
# En las opciones de Mauve 
Tools > Move Contigs. ordenar contigs e introducir el genoma de referencia.
Comparación entre genomas 
# Con programa Brig , necesito leer mas a profundidad



