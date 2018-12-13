# Ossec
## ¿Para que nos puede servir OSSEC?
Saber en todo momento que está pasando en nuestros sistemas.
Parar ataques a nuestros sistemas.
OSSEC es multiplataforma, ya que puede instalarse en sistemas GNU Linux, 
Solaris, Microsoft Windows , MAC OS X, WMWARE, *BSD, AIX y HP-UX. 
Se pueden modificar los parámetros del programa, modificando el fichero ossec.conf

## Configurar OSSEC
Si visitamos el directorio /var/ossec, como usuario root, veremos lo siguientes directorios:

/bin – Aquí tenemos almacenados todos los binarios ejecutables.
/etc – Los ficheros de configuración, entre los que se encuentran  ossec.conf
/logs – Importantísimo directorio donde tenemos todos los ficheros log. Cabe resaltar ossec.log y alerts/alerts.log
/queue –  Se almacenan los ficheros de colas de proceso.
/rules – Aquí tenemos los ficheros  que utiliza el programa para generar las alertas.
/stats – Para generar las estadísticas
/tmp – Directorio temporal
/var – “pid” para los procesos de OSSEC

El fichero clave para la configuración es /var/ossec/etc/ossec.conf, que se divide en varios apartados, 
según el servicio a configurar.

global (global);
rules (rules);
syscheck (syscheck/rootcheck);
alerts (alert);
active-response (command/active-response);
collector (localfile);

##Alertas 
##Cliente
##Global
##Archivo local
##Remoto
##Rootcheck
##Syslog
