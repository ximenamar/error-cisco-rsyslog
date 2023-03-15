# error-cisco-rsyslog
1. En caso de errores o que no esté direccionando los logs al RSYSLOG, aplicar la siguiente configuración

switch(config)#no logging console
switch(config)#no logging 
switch(config)#no logging trap debbuging
switch(config)#no logging facility local7
switch(config)#no logging host [IP-RSYSLOG-CONFIGURADO] transport tcp port 8514


2.	Volver a configurar el envío de CISCO a RSYSLOG. Configurar el módulo de logs. El host debe apuntar al servidor RSYSLOG

switch(config)#logging on
switch(config)#logging [IP-RSYSLOG]

3. Configurar el Facility

switch(config)#logging facility local7

4. Configurar la severidad de los logs a recolectar

switch(config)#logging trap notifications

NOTA:
Especifica el tipo de mensajes, por nivel de gravedad, que se enviarán al servidor Rsyslog. El valor predeterminado es informativo (7), y en este caso, se cambió al nivel 5 (Notice). Los niveles son los siguientes:
•	Emergency: 0
•	Alert: 1
•	Critical: 2
•	Error: 3
•	Warning: 4
•	Notice: 5
•	Informational: 6
•	Debug: 7


5. Verificar que cambió la severidad en la configuración

switch(config)#show logging

6. Cambiar al puerto TCP

switch(config)#logging host [IP-RSYSLOG] transport tcp port 8514

7. Guardar la configuración

switch(config)#copy running-config startup-config
