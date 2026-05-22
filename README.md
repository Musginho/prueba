## Infraestructura de la Red Local "TechPYME"

Documentacion tecnica de la nueva infraestructura de red. Este proyecto es **altamente critico** para el funcionamiento de la empresa y cualquier cambio en los servidores debe hacerse con *extrema precaucion*

> [!WARNING]
> **Ventana de mantenimiento**: CUalquier reinicio del swithc principal o del router de la operadores de realizarse estrictamente fuera del horario laboral (despues de las 18:00h) para evitar la desconexcion de los equipo de Contabilidad y Direccion
![Estado](https://img.shields.io/badge/Estado-Operativa-brightgreen)
Para mas destalles sobre los estandares de cableado estructurado aplicados, puedes consultar la normativa de la [Asociacion de la industria de Telecomuncaciones (TIA)](https://tiaonline.org/)

# Topologia de la Red
A continuacion se presenta un diagrama de arquitectura de la red locla, mostrando la conexion desde el exterior hasta los equipos finales:

```mermaid
flowchart TD
A(Internet) <--> B[Router Operadora 192.168.1.1]
B <--> C[Switch Principal Cisco 24 Puertos]
subgraph "Equipos de oficina"
C <--> D[PC Contabilidad Windows 11]
C <--> F[PC Direccion Windows 11]
C <--> G[Impresora Lase de red]

subgraph "Sala de servidores"
C <--> H[Windows Server 2022]
C <--> I[(NAS Synology Backups Diarios)]
