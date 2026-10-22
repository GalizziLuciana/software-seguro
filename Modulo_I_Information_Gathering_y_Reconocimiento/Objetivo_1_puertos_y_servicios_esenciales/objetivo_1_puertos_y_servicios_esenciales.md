# Objetivo 1: Puertos y servicios esenciales

Los puertos permiten identificar a qué servicio se dirige una conexión. Estos son los servicios asociados comunmente a los puertos solicitados:

| Puerto | Servicio | ¿Para qué sirve? |
| --- | --- | --- |
| 20 | FTP (datos) | Transfiere archivos y datos en el modo activo de FTP. |
| 21 | FTP (control) | Recibe los comandos para iniciar sesión y gestionar la transferencia de archivos. |
| 22 | SSH | Permite acceder y administrar un equipo de forma remota con comunicación cifrada. |
| 23 | Telnet | Permite acceder a un equipo de forma remota, sin cifrado por defecto. |
| 25 | SMTP | Se utiliza principalmente para enviar correo entre servidores. |
| 53 | DNS | Resuelve nombres de dominio a direcciones IP, entre otras consultas. Usa UDP y TCP. |
| 80 | HTTP | Permite acceder a sitios web sin cifrado TLS. |
| 110 | POP3 | Permite descargar correos desde un servidor al cliente de correo. |
| 443 | HTTPS | Permite acceder a sitios web con la comunicación protegida mediante TLS. |
| 3306 | MySQL | Permite conectar aplicaciones y clientes con una base de datos MySQL. |

Fuente de las asignaciones: [registro oficial de puertos de IANA](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml).

Estos puertos son convenciones: un servicio puede configurarse para usar otro puerto
