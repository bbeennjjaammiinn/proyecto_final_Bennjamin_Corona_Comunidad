# ***Proyecto Final Bioinf2017-II***

# *** AVANCES 3 

### Tipo de datos: Datos genómicos propios obtenidos a través de secuenciación de genomas completos, se procesaran los datos crudos.

En este momento cuento con un genoma de Vibrio Anguillarum secuenciado con tecnología iIllumina, los datos crudos en formato .fastq.gz tipo paired end fueron descomprimidos y visualizadas sus calidades de reads con el programa FastQC.
     
# * Preprocesamiento de archivos FASTQ con FASTX-Toolkit
     

Use fastx_quality_stats para visualizar las estadísticas de calidad de mis archivos antes y despues del preprosesamiento. También obtuve una gráfica de calidades con fastq_quality_boxplot_graph
    FASTQ Quality Filter y FASTQ Trimer 
Use FASTQ Quality Filter para filtrar la secuencias en base a su calidad y FASTQ Trimmer para cortar las secuencias en formato Fastq al remover el ruido y los barcodes. 

# * Ensamblado del genoma con Velvet

Instale el programa velvet 1.2.10 en el entorno de trabajo unix de linux. Cree el Roadmap con el programa Velveth, y con Velvetg pienso generar las gráficas Bruijn para ensamblar y que pueda crear contigs y scaffoldings concatenados (sin embargo en este paso tengo problemas y no he logrado que corra, pienso que es un problema de memoria y tratare de correrlo con una computadora mas potente). Mientras tanto descargue e instale el programa SPAdes-3.10.1 con el cual pienso intentar ensamblar.

# * Ensamble con referencia MAUVE

Baje e instale el programa MAUVE y baje un genoma de referencia para compararlo con mi genoma de Vibrio este programa corre en un entorno gráfico con con java.

# * Comparación entre genomas 

Bajare el programa Brig y quiero comparar al menos tres genomas.

# * Readme

Esto es mi borrador del readme

# * He leído los siguientes artículos:


Sohn, J. I., & Nam, J. W. (2016). The present and future of de novo whole-genome assembly. Briefings in Bioinformatics, bbw096.
*Reimer, A. R. (2011). Comparative Genomics of Vibrio cholerae from Haiti, Asia, and Africa-Volume 17, Number 11—November 2011-Emerging Infectious Disease journal-CDC.
*Chen, C. Y., Wu, K. M., Chang, Y. C., Chang, C. H., Tsai, H. C., Liao, T. L., ... & Su, T. L. (2003). Comparative genome analysis of Vibrio vulnificus, a marine pathogen. Genome research, 13(12), 2577-2587.
*Ke, H. M., Prachumwat, A., Yu, C. P., Yang, Y. T., Promsri, S., Liu, K. F., ... & Li, W. H. (2017). Comparative genomics of Vibrio campbellii strains and core species of the Vibrio Harveyi clade. Scientific Reports, 7.
*Dutilh, B. E., Thompson, C. C., Vicente, A. C., Marin, M. A., Lee, C., Silva, G. G., ... & Garza, D. R. (2014). Comparative genomics of 274 Vibrio cholerae genomes reveals mobile functions structuring three niche dimensions. BMC genomics, 15(1), 654.
*Se han descargado los siguientes programas y sus tutoriales:
*Maube *velvet_1.2.10  *ClonalFrameML * SPAdes-3.10.1