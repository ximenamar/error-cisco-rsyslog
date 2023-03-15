<h1>Error de envío de logs Cisco a RSYSLOG </h1>

**1. En caso de errores o que no esté direccionando los logs al RSYSLOG, aplicar la siguiente configuración**

`switch(config)#no logging console`<br />
`switch(config)#no logging`<br />
`switch(config)#no logging trap debbuging`<br />
`switch(config)#no logging facility local7`<br />
`switch(config)#no logging host [IP-RSYSLOG-CONFIGURADO] transport tcp port 8514`<br />


**2.	Volver a configurar el envío de CISCO a RSYSLOG. Configurar el módulo de logs. El host debe apuntar al servidor RSYSLOG**

`switch(config)#logging on`<br />
`switch(config)#logging [IP-RSYSLOG]`<br />

**3. Configurar el Facility**

`switch(config)#logging facility local7`<br />

**4. Configurar la severidad de los logs a recolectar**

`switch(config)#logging trap notifications`<br />

**NOTA:**
Especifica el tipo de mensajes, por nivel de gravedad, que se enviarán al servidor Rsyslog. El valor predeterminado es informativo (7), y en este caso, se cambió al nivel 5 (Notice). Los niveles son los siguientes:<br />
•	Emergency: 0<br />
•	Alert: 1<br />
•	Critical: 2<br />
•	Error: 3<br />
•	Warning: 4<br />
•	Notice: 5<br />
•	Informational: 6<br />
•	Debug: 7<br />


**5. Verificar que cambió la severidad en la configuración**

`switch(config)#show logging`<br />

**6. Cambiar al puerto TCP**

`switch(config)#logging host [IP-RSYSLOG] transport tcp port 8514`<br />

**7. Guardar la configuración**

`switch(config)#copy running-config startup-config`<br />
