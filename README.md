# DNS-sistema.test

Este repositorio contiene la configuración y documentación necesaria para implementar un servidor DNS con los siguientes requisitos en un entorno de prueba. A continuación, se detallan los aspectos clave del sistema, la configuración de DNS y los equipos involucrados.

## Tabla de Contenidos

1. [Equipos y Configuración](#equipos-y-configuración)
2. [Configuración del Servidor DNS](#configuración-del-servidor-dns)
3. [Alias y Servidor de Correo](#alias-y-servidor-de-correo)
4. [Consideraciones Finales](#consideraciones-finales)

---

## Equipos y Configuración

| Equipo               | FQDN                  | IP      | Sistema Operativo |
|----------------------|-----------------------|---------|--------------------|
| Gráfico (Imaginario) | mercurio.sistema.test  | .101    | Imaginario         |
| Texto                | venus.sistema.test     | .102    | Debian             |
| Texto                | tierra.sistema.test    | .103    | Debian             |
| Gráfico/Server       | marte.sistema.test     | .104    | Imaginario         |

---
![1](https://github.com/aluqmor/DNS-sistema.test/blob/main/capturas/1.png)
![2](https://github.com/aluqmor/DNS-sistema.test/blob/main/capturas/2.png)
![3](https://github.com/aluqmor/DNS-sistema.test/blob/main/capturas/3.png)
![4](https://github.com/aluqmor/DNS-sistema.test/blob/main/capturas/4.png)
---

## Configuración del Servidor DNS

1. **Escucha del Servidor**: El servidor DNS solo escuchará solicitudes para el protocolo **IPv4**.
2. **Validación DNSSEC**: Se debe establecer la opción `dnssec-validation` en **yes** para asegurar la integridad de las consultas DNS.
3. **Consultas Recursivas**: Las consultas recursivas se permitirán únicamente a los equipos en las redes `127.0.0.0/8` y `192.168.57.0/24`, utilizando listas de control de acceso (ACL).
4. **Servidor Maestro**: `tierra.sistema.test` actuará como el servidor maestro con autoridad sobre la zona directa e inversa.
5. **Servidor Esclavo**: `venus.sistema.test` funcionará como servidor esclavo, apuntando a `tierra.sistema.test` como su maestro.
6. **Tiempo de Caché**: El tiempo en caché para respuestas negativas de las zonas (directa e inversa) será de **7200 segundos** (2 horas).
7. **Reenvío de Consultas**: Consultas no autorizadas se reenviarán al servidor DNS `208.67.222.222` (OpenDNS).

---

## Alias y Servidor de Correo

Se configurarán los siguientes alias:

- **ns1.sistema.test**: Alias de `tierra.sistema.test`.
- **ns2.sistema.test**: Alias de `venus.sistema.test`.
- **mail.sistema.test**: Alias de `marte.sistema.test`.

El equipo `marte.sistema.test` actuará como el servidor de correo del dominio `sistema.test`.

---

## Comprobaciones

![c1](https://github.com/aluqmor/DNS-sistema.test/blob/main/capturas/c1.png)
![c2](https://github.com/aluqmor/DNS-sistema.test/blob/main/capturas/c2.png)
![c3](https://github.com/aluqmor/DNS-sistema.test/blob/main/capturas/c3.png)
![c4](https://github.com/aluqmor/DNS-sistema.test/blob/main/capturas/c4.png)
![c5](https://github.com/aluqmor/DNS-sistema.test/blob/main/capturas/c5.png)
![c6](https://github.com/aluqmor/DNS-sistema.test/blob/main/capturas/c6.png)
