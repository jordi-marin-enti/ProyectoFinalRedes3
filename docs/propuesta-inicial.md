# Propuesta inicial

## 1. Idea elegida
La mejor opción es una **red segura multisede** porque permite reutilizar el trabajo previo de clase y, al mismo tiempo, incorporar todos los requisitos nuevos del proyecto final.

## 2. Escenario
Empresa con:
- sede central
- una sucursal
- teletrabajadores
- servicios web/DNS en DMZ
- WiFi corporativa y WiFi invitados

## 3. Topología propuesta
### Sede central
- VLAN 10 Administración
- VLAN 20 Usuarios
- VLAN 30 Servidores
- VLAN 40 Invitados
- AP corporativo con 802.1X
- servidor RADIUS/FreeRADIUS

### Perímetro
- Firewall FortiGate
- DMZ con servidor web y DNS
- políticas NAT y filtrado
- logging y monitorización

### Conectividad remota
- VPN site-to-site con la sucursal
- VPN SSL o IPsec para teletrabajo
- SD-WAN para elegir mejor salida WAN

## 4. Justificación
Esta idea es sólida porque enlaza directamente con las prácticas:
- ACT1 aporta la segmentación por VLAN
- ACT2 aporta el firewall y las reglas
- ACT3 aporta la DMZ
- ACT5/ACT6 aportan pruebas, hardening y monitorización
- ACT7 aporta IDS/IPS y análisis con Wireshark

## 5. Reglas de seguridad iniciales
- Permitir HTTP/HTTPS únicamente hacia servidores publicados en DMZ
- Permitir SSH solo desde VLAN de administración
- Denegar acceso desde WiFi invitados a VLAN corporativas
- Permitir VPN entre sedes y acceso remoto autenticado
- Registrar eventos relevantes del firewall
