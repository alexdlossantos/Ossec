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

    e) <ossec_config> 
       <alerts> 
        < - 
        opciones de alertas aquí 
        -> 
        </alerts> 
        </ossec_config>

# Crear "Ossec.conf"
## Global

    ) <ossec_config> 
      <global> 
      <- 
      Opciones globales aquí 
      -> 
      </global> 
      </ossec_config>

#### email_notification
Habilitar o deshabilitar las alertas de correo electrónico.

Predeterminado: no

Permitido: si / no

#### email_to
E-mail del destinatario de las alertas.

Permitido: Cualquier dirección de correo electrónico válida

#### email_from¶
E-mail "fuente" de las alertas.

Permitido: Cualquier dirección de correo electrónico válida

#### smtp_server
Servidor SMTP.

Permitido: cualquier nombre de host o dirección IP válido

#### email_maxperhour
Especifica el número máximo de correos electrónicos que se enviarán por hora. Todos los correos electrónicos que excedan esta configuración se pondrán en cola para su posterior distribución.

Predeterminado: 12

Permitido: Cualquier número del 1 al 9999

#### custom_alert_output
Especifica el formato de las alertas escritas en el archivo de registro.

#### stats
Nivel de alerta para los eventos generados por el análisis estadístico.

Predeterminado: 8

Permitido: Cualquier nivel de 0 a 16.

#### logall
Indica si debemos almacenar todos los eventos recibidos.

Predeterminado: no

Permitido: si / no

#### memory_size
Establece el tamaño de memoria para la correlación de eventos.

Predeterminado: 1024

Permitido: cualquier tamaño de 16 a 5096

#### white_list
Lista de direcciones IP que nunca deben ser bloqueadas por la respuesta activa (una por elemento). Esta opción solo es válida en instalaciones locales y de servidor.

Múltiplos Permitidos: si

Permitido: Cualquier dirección IP o netblock

#### host_infomation
Nivel de alerta para los eventos generados por el monitor de cambio de host.

Predeterminado: 8

Permitido: Cualquier nivel de 0 a 16.

#### jsonout_output
Habilite o inhabilite la escritura de alertas con formato json en /var/ossec/logs/alerts/alerts.json

Predeterminado: no Permitido: sí / no

## Archivo local

    ) <ossec_config> 
      <localfile> 
      <- 
      Opciones de Localfile aquí 
      -> 
      </localfile> 
      </ossec_config>
      
#### location
Especifique la ubicación del registro a leer

#### syslog
Este formato es para archivos de texto plano en un formato similar a syslog. También se puede utilizar cuando no hay soporte para el formato de registro y los registros son mensajes de una sola línea.

#### resoplido
Esto se utiliza para el formato de salida completo de Snort.

#### resoplido
Esto se utiliza para el formato de salida rápida de Snort.

#### mysql_log
Esto se utiliza para los registros de MySQL . No es compatible con los registros de varias líneas.

#### postgresql_log
Esto se utiliza para los registros de PostgreSQL . No es compatible con los registros de varias líneas.

#### nmapg
Esto se usa para monitorear archivos que se ajustan a la salida grepable de nmap .

#### apache
Este formato es para el formato de registro predeterminado de apache.

#### mando
Este formato será el resultado del comando (como se ejecuta por la raíz) definido por el comando . Cada línea de salida se tratará como un registro separado.

#### full_command
Este formato será el resultado del comando (como se ejecuta por la raíz) definido por el comando . Toda la salida se tratará como un solo registro.

#### command
El comando a ejecutar. Todos los resultados de este comando se leerán como uno o más mensajes de registro, dependiendo de si se usa el comando o full_command .

Permitido: Cualquier línea de comando y argumentos.

#### frequency
El tiempo mínimo en segundos entre las ejecuciones del comando. Es probable que el comando no se ejecute frequencyexactamente cada segundo, pero el tiempo entre ejecuciones no será más corto que este ajuste. Esto se usa con el comando y full_command.



## Alertas 

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

## Cliente

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


## Remoto

    ) <ossec_config>
      <remote>
      <--
      remote options here
      -->
      </remote>
      </ossec_config>

#### Opciones 
#### connection
Especifique el tipo de conexión que se habilita: segura o usando syslog.

Predeterminado: seguro

Permitido: seguro / syslog

#### port
Especifica el puerto para escuchar eventos.

Defecto:

1514: si la conexión está configurada para asegurar
514: si la conexión se establece en syslog
Permitido: cualquier número de puerto de 1 a 65535

#### protocol
Especifica el protocolo a utilizar para eventos de syslog.

Predeterminado: udp

Permitido: udp o tcp

#### allowed-ips
Lista de direcciones IP que pueden enviar mensajes de syslog al servidor (uno por elemento).

Permitido: cualquier dirección IP o red

#### Nota

Es necesario permitir al menos una dirección IP cuando se utiliza el tipo de conexión syslog.

#### deny-ips
Lista de direcciones IP que no pueden enviar mensajes de syslog al servidor (uno por elemento).

Permitido: cualquier dirección IP o red

#### local_ip
Dirección IP local para escuchar conexiones.

Predeterminado: todas las interfaces

Permitido: Cualquier dirección IP interna

#### ipv6
Dirección ipv6 local para escuchar conexiones.

Predeterminado: Ninguno

Permitido: Cualquier dirección IPv6.

## Rootcheck
    ) <ossec_config> 
      <rootcheck> 
      <- 
      opciones de comprobación de raíz aquí 
      -> 
      </rootcheck> 
      </ossec_config>
      
      Permitido: Ruta a un directorio Predeterminado: / var / ossec

#### rootkit_files
Esta opción se puede utilizar para cambiar la ubicación de la base de datos de archivos de rootkit.

Permitido: Un archivo con las firmas de los archivos de rootkit.

Por defecto: /etc/shared/rootkit_files.txt

#### rootkit_trojans
Esta opción se puede utilizar para cambiar la ubicación de la base de datos de troyanos de rootkit.

Por defecto: /etc/shared/rootkit_trojans.txt

Permitido: Un archivo con las firmas de los troyanos.

windows_audit
system_audit
windows_apps
windows_malware
scanall
Le dice a rootcheck que analice todo el sistema (puede llevar a algunos falsos positivos).

Predeterminado: no

Permitido: si / no

#### frequency
Frecuencia con la que se ejecutará el rootcheck (en segundos).

Valores predeterminados: 36000 (10 horas)

Permitido: Tiempo (en segundos)

#### disabled
Desactiva la ejecución de rootcheck.

Predeterminado: no

Permitido: si / no

#### check_dev
Habilitar o deshabilitar la comprobación de algo.

Predeterminado: si

Permitido: si o no

#### check_files
Habilitar o deshabilitar la comprobación de algo.

Predeterminado: si

Permitido: si o no

#### check_if
Habilitar o deshabilitar la comprobación de algo.

Predeterminado: si

Permitido: si o no

#### check_pids
Habilitar o deshabilitar la comprobación de algo.

Predeterminado: si

Permitido: si o no

#### check_policy
Habilitar o deshabilitar la comprobación de algo.

Predeterminado: si

Permitido: si o no

#### check_ports
Habilitar o deshabilitar la comprobación de puertos de red.

Predeterminado: si

Permitido: si o no

#### check_sys
Habilitar o deshabilitar la comprobación de algo.

Predeterminado: si

Permitido: si o no

#### check_trojans
Habilitar o deshabilitar la comprobación de troyanos.

Predeterminado: si

Permitido: si o no

#### check_unixaudit
Habilitar o deshabilitar la comprobación de algo.

Predeterminado: si

Permitido: si o no

#### check_winapps
Habilitar o deshabilitar la comprobación de algo.

Predeterminado: si

Permitido: si o no

#### check_winaudit
Habilitar o deshabilitar la comprobación de algo.

Predeterminado: 1

Permitido: 1 o 0

#### skip_nfs
Especifica si rootcheck debe analizar los sistemas de archivos montados en la red. Funciona en Linux y FreeBSD. Actualmente, skip_nfs cancelará las comprobaciones que se ejecuten en montajes CIFS o NFS.

Predeterminado: no

Permitido: si / no

## Syslog

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

