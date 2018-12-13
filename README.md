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

1.  /bin – Aquí tenemos almacenados todos los binarios ejecutables.
2.  /etc – Los ficheros de configuración, entre los que se encuentran  ossec.conf
3.  /logs – Importantísimo directorio donde tenemos todos los ficheros log. Cabe resaltar ossec.log y alerts/alerts.log
4.  /queue –  Se almacenan los ficheros de colas de proceso.
5.  /rules – Aquí tenemos los ficheros  que utiliza el programa para generar las alertas.
6.  /stats – Para generar las estadísticas
7.  /tmp – Directorio temporal
8.  /var – “pid” para los procesos de OSSEC

El fichero clave para la configuración es /var/ossec/etc/ossec.conf, que se divide en varios apartados, 
según el servicio a configurar.

    a) global (global);
    b) rules (rules);
    c) syscheck (syscheck/rootcheck);
    d) alerts (alert);
    e) active-response (command/active-response);
    f) collector (localfile);

### La sección global
En éste apartado indicamos el correo electrónico que recibirá las notificaciones y las listas blancas de IP.

    a) <ossec_config>
       <global>
       <--
       Global options here
        -->
       </global>
       </ossec_config>

### Sección Collector
Lista de todos los ficheros que utilizará el programa para monitorizar.

    b) <ossec_config> 
       <localfile> 
       <! - 
       Opciones de Localfile aquí 
        -> 
       </localfile> 
       </ossec_config>

### Syscheck
En ésta sección indicamos la frecuencia de los chequeos, los directorios a revisar y los que queremos excluir.

    c) <syscheck>
       </syscheck>

### Rules
Sección donde se indican las ubicaciones de los ficheros que contienen las reglas.

    d) <ruleset>
       </ruleset>

### Alerts
Aquí señalamos el nivel de las alertas. 0 es el nivel más bajo, considerado inútil y 16 es el más alto, considerado crítico. Depende del nivel de alerta se envía o no un correo electrónico. Funcionan los envíos a partir del nivel 7. Dicho parámetro se puede modificar.

    a) <ossec_config> 
       <alerts> 
        < - 
        opciones de alertas aquí 
        -> 
        </alerts> 
        </ossec_config>

## Crear "Ossec.conf"
### Global


### Archivo local


### Alertas 

     ) <ossec_config> 
       <alerts> 
        <- 
        opciones de alertas aquí 
        -> 
        </alerts> 
        </ossec_config>

#### Opciones 

#### email_alert_level
Nivel mínimo de alerta para enviar notificaciones por correo electrónico.

Predeterminado: 7

Permitido: Cualquier nivel de 1 a 16.

#### Nota

Este es el nivel mínimo para que una alerta active un correo electrónico. Esto anula los niveles de alerta granular de correo electrónico. Establecer esto en 10 evitaría que los correos electrónicos para alertas a niveles inferiores a 10 se envíen a pesar de las configuraciones en la configuración de correo electrónico granular. Las reglas individuales pueden anular esto con la opción alert_by_email .

#### log_alert_level
Nivel mínimo de alerta para almacenar los mensajes de registro.

Predeterminado: 1

Permitido: Cualquier nivel de 1 a 16.

### Cliente

     ) <ossec_config> 
       <client> 
        <- 
        opciones de cliente aquí 
        -> 
        </client> 
        </ossec_config>

#### Opciones 

#### server-ip
Especifique la dirección IP del servidor de análisis.

Permitido: Cualquier dirección IP válida

#### server-hostname
Especifique el nombre de host del servidor de análisis

Permitido: Cualquier nombre de host válido

#### port
Especifica el puerto para enviar los eventos (debe ser el mismo que el utilizado por el servidor de análisis).

Predeterminado: 1514

Permitido: cualquier número de puerto de 1 a 65535

#### config-profile
Especifica los agent.confperfiles que utilizará el agente. Se pueden incluir múltiples perfiles, separados por una coma y un espacio.

#### Ejemplo:

     ) <client> 
       <config-profile> webserver, lowmemory </config-profile> 
       </client>

#### notify_time
Especifica el tiempo en segundos entre los mensajes de información enviados por los agentes al servidor.

#### time-reconnect
Tiempo en segundos hasta un intento de reconexión. Esto debe establecerse en un número más alto que el notificar tiempo.



### Remoto
### Rootcheck
### Syslog

     )  <ossec_config> 
        <syslog_output> 
        <- 
        Opciones de salida de Syslog aquí 
        -> 
        </syslog_output> 
        </ossec_config>

#### Opciones
##### server
Dirección IP del servidor syslog.
Permitido: cualquier dirección IP válida
#### port
Puerto para reenviar alertas a.
Predeterminado 514
Permitido: Cualquier puerto válido
#### level
Nivel mínimo de alerta de las alertas a reenviar.
Permitido: 1 - 16
#### group
Se reenviarán las alertas pertenecientes a este grupo.
Permitido: Cualquier grupo válido. Separe los múltiples grupos con el caracter de pipe ( |).
#### Ejemplos:
<group> syscheck </group> 
<group> authentication_failure | authentication_success </group>
rule_id
Las alertas que coincidan con esta rule_id se reenviarán.
Permitido: cualquier regla_id válida
#### location
Las alertas de esta ubicación serán reenviadas.
Permitido: cualquier ubicación de archivo de registro válida

