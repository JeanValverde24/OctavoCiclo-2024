
# SEMANA 4: Routing VLANs

## Conceptos Clave para Examen:

### Enrutamiento entre VLANs:
- Permite la comunicación entre dispositivos en diferentes VLANs.
- Los métodos incluyen:
  - **Router-on-a-stick:** Configura subinterfaces en una interfaz física para enrutar tráfico entre VLANs.
  - **Switch de Capa 3 con SVI:** Ofrece una solución más eficiente y escalable para grandes redes, utilizando interfaces virtuales.

### Router-on-a-stick:
- Este método usa una única interfaz física en el router con subinterfaces lógicas para enrutar el tráfico de múltiples VLANs.

## Escenario de enrutamiento entre VLANs - Router-on-a-stick:
- En este escenario, los hosts en diferentes VLANs no pueden hacer ping entre sí debido a la falta de configuración de subinterfaces y enlaces troncales.
- El enrutamiento se realiza creando subinterfaces y asignando direcciones IP correspondientes a cada VLAN.

## Diagrama en mermaid:

```mermaid
graph TD
  Router[Router] -->|Troncal 802.1Q| Switch1[Switch]
  Switch1 -->|VLAN 10| PC1[PC en VLAN 10]
  Switch1 -->|VLAN 20| PC2[PC en VLAN 20]
  Router -->|Subinterfaces| Interface1[Subinterface G0/0.10 - VLAN 10]
  Router -->|Subinterfaces| Interface2[Subinterface G0/0.20 - VLAN 20]
```
