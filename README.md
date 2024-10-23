# DNS-sistema.test

Creamos las máquinas virtuales Mercurio (imaginaria), Venus, Tierra y Marte (imaginaria) con el box bookworm64. A cada máquina le asignamos una ip fija. 

Configuramos el named.conf.options de tierra y venus para hacer que solo escuche direcciones ipv4, permita consultas dentro de su misma red, consultas recursivas, activar dnssec y asignar la direccion 208.67.222.222 para reenviar las consultas:
(./capturas/)