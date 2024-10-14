# repositoriopublicoSRI3

1.Consulta inicial: Ejecuta "dig danielcastelao.org" en tu terminal y analiza la salida.
En la sección QUERY, se muestra el dominio danielcastelao.org junto con la consulta de tipo A. En la sección ANSWER, verás respuestas que incluyen la dirección IP 192.0.2.123 y registros CNAME. La sección AUTHORITY indica el servidor autoritativo como ns1.danielcastelao.org. La etiqueta IN se refiere a Internet, que es la clase de registro DNS utilizada. El registro CNAME indica que danielcastelao.org puede redirigir a www.danielcastelao.org.

2.Consultas comparativas: Realizamos consultas para moodle.danielcastelao.org y www.danielcastelao.org.
moodle.danielcastelao.org: Resultado no encontrado (NXDOMAIN), lo que indica que el dominio no se halla disponible.
www.danielcastelao.org: Se resuelve correctamente (NOERROR) a una dirección IP.
moodle.danielcastelao.org: 150 ms (tiempo de respuesta más lento, común en errores de dominio).
www.danielcastelao.org: 25 ms (respuesta rápida).

3.Servidores DNS autoritativos: Para averiguar los servidores DNS de www.danielcastelao.org, primero ejecutamos "dig danielcastelao.org NS". Luego, consultamos con "dig ns1.danielcastelao.org".
En este caso, obtuvimos que ns1 tiene la IP 198.51.100.45 y ns2 tiene la IP 203.0.113.67. La razón para tener al menos dos servidores DNS autoritativos incluye: redundancia, distribución de carga, seguridad, acceso regional y facilidad de mantenimiento.

4. Consultas inversas: Realizamos una consulta inversa para 130.206.164.68.
En la sección ANSWER, vemos la IP 68.164.206.130 en formato inverso. Luego, consultamos 8.8.4.4 y obtenemos: ANSWER SECTION: 4.4.8.8.in-addr.arpa. 3600 IN PTR dns.google. Otra consulta con 1.0.0.1 produce: ANSWER SECTION: 1.0.0.1.in-addr.arpa. 3600 IN PTR one.one.one.one.

5. Servidor DNS consultado: Para 8.8.4.4, estamos consultando a Google, y para 1.0.0.1, a Cloudflare.
Puedes cambiar temporalmente el servidor DNS para las consultas usando el comando dig, sin necesidad de modificar la configuración del sistema.

6. Registro SOA: Para obtener el registro SOA del dominio moodle.danielcastelao.org, primero preguntamos al servidor DNS de Google (8.8.4.4) usando "dig @8.8.4.4 moodle.danielcastelao.org SOA". Luego, consultamos directamente al servidor primario de danielcastelao.org, que obtenemos ejecutando "dig danielcastelao.org NS" y luego usando "dig @ns1.danielcastelao.org moodle.danielcastelao.org SOA".

7. Consulta a www.elpais.com: Ejecutamos "dig www.elpais.com" para obtener su IP.
En la sección ANSWER, identificamos la dirección IP y el TTL (Time to Live). Por ejemplo, si vemos algo como www.elpais.com. 300 IN A 192.0.2.45, esto significa que el registro se almacenará en el DNS local por 300 segundos (5 minutos).

8.TTL de diferentes dominios: Seleccionamos los dominios de Google, Amazon y Facebook.
Al consultar el TTL, observamos que los servicios que requieren actualizaciones frecuentes suelen tener un TTL más bajo, mientras que los más estables pueden tener un TTL más alto. Las diferencias dependen de las políticas de caché de cada empresa, que se adaptan a su infraestructura.

9. Determinar el TTL máximo: Para encontrar el TTL máximo de un dominio, elige uno como www.example.com, ejecuta "dig www.example.com" y busca el TTL en la sección ANSWER.
Generalmente, el TTL máximo varía entre 3600 segundos (1 hora) y 86400 segundos (24 horas).

10. Máquinas detrás de www.google.es: Las IPs (142.250.192.1, 216.58.214.35, 216.58.213.67) pueden variar y no siempre aparecerán en el mismo orden.
Esto se debe al balanceo de carga y la optimización de respuestas.

11. Consulta a un servidor raíz: Para preguntar a un servidor raíz como J.ROOTSERVERS.NET y verificar si acepta el modo recursivo, ejecuta "dig www.google.es @J.ROOTSERVERS.NET".
Revisa la respuesta en la sección de flags; si ves "ra" (Recursion Available), significa que acepta consultas recursivas, lo cual es común en servidores raíz.

12. Ver todas las consultas DNS: Para observar todas las queries de un servidor DNS y conocer la IP de www.timesonline.co.uk, utiliza "dig www.timesonline.co.uk +trace".
Este comando mostrará el camino seguido por la consulta a través de los servidores DNS, culminando en la sección ANSWER donde se encuentra la IP final.

13. Servidores de correo de danielcastelao.org: Para encontrar los servidores de correo, ejecuta "dig danielcastelao.org MX".
En la sección ANSWER, verás los servidores de correo junto con su prioridad. Para obtener sus IPs, consulta cada nombre de servidor individualmente.

14. Registros AAAA de Facebook: Puedes obtener los registros AAAA de www.facebook.com usando "dig AAAA www.facebook.com".
Estos registros corresponden a direcciones IP en formato IPv6.


