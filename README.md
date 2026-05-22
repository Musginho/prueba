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
%% Conexion Externa
Internet((Internet))
Router[Router Operadora <br/> 192.168.1.1]
Switch[Switch Principal <br/> Cisco 24 Puertos

%% Zona de servidores
  subgraph "Sala de servidores (Rack Principal"
  Server[Windows Server 2022 <br/> AD / DNS / DHCP
  NAS[NAS Synology <br/> Backups diarios]
end

%% Equipos de Oficina
subgraph "Equipos de Oficina"
  PC1[PC Contabilidad <br/> Windows 11]
  PC2[PC Direccion <br/> Windows 11]
  Impresora[Impresora Laser <br/> de Red]
end

%% Conexiones de Red
Internet <--> Router
Router <--> Switch
Switch <--> PC1
Switch <--> PC2
Switch <--> Impresora
Switch <--> Server
Switch <--> NAS
