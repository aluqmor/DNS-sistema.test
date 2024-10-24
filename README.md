# DNS-sistema.test

Creamos las máquinas virtuales Mercurio (imaginaria), Venus, Tierra y Marte (imaginaria) con el box bookworm64. A cada máquina le asignamos una ip fija. 

Configuramos el named.conf.options de tierra y venus para hacer que solo escuche direcciones ipv4, permita consultas dentro de su misma red, consultas recursivas, activar dnssec y asignar la direccion 208.67.222.222 para reenviar las consultas:
(./capturas/1)

Hay que configurar el servidor maestro (tierra) en named.conf.local:
(./capturas/2)

Y lo mismo con el servidor esclavo (venus):
(./capturas/3)

Ahora configuramos el db.sistema.test para hacer que el tiempo en cache
de las respuestas negativas sea de 2 horas (7200 segundos), configuramos
que "ns1", "ns2" y "mail" serán alias de tierra, venus y marte respectivamente. Marte actuará como servidor de correo del dominio sistema.test:
(./capturas/4)

-------------------------------- COMPROBACIONES---------------------------
1. Registros tipo A:
(./capturas/c1)

2. Forma inversa:
(./capturas/c2)

3. Resolver los alias ns1.sistema.test y ns2.sistema.test:
(./capturas/c3)

4. Servidores NS de sistema.test:
(./capturas/c4)

5. Servidores MX de sistema.test:
(./capturas/c5)