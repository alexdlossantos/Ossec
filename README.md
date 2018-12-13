# Ossec

![ossec-01022014](https://user-images.githubusercontent.com/42847572/49968925-d4291800-feec-11e8-964c-8fca1f2a074f.jpg)

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
La sección global
En éste apartado indicamos el correo electrónico que recibirá las notificaciones y las listas blancas de IP.


Sección Collector
Lista de todos los ficheros que utilizará el programa para monitorizar.


Syscheck
En ésta sección indicamos la frecuencia de los chequeos, los directorios a revisar y los que queremos excluir.


Rules
Sección donde se indican las ubicaciones de los ficheros que contienen las reglas.


Alerts
Aquí señalamos el nivel de las alertas. 0 es el nivel más bajo, considerado inútil y 16 es el más alto, considerado crítico. Depende del nivel de alerta se envía o no un correo electrónico. Funcionan los envíos a partir del nivel 7. Dicho parámetro se puede modificar.

<ossec_config> 
    <alerts> 
        <! - 
        opciones de alertas aquí 
        -> 
    </alerts> 
</ossec_config>

### Alertas 
### Cliente
### Global
### Archivo local
### Remoto
### Rootcheck
### Syslog
