
# SEMANA 2 - Conceptos de Conmutación (Switching)

1. **Reenvío de Tramas (Frame Forwarding)**
    - Conmutación en Redes: El switch utiliza las direcciones MAC para decidir cómo reenviar las tramas. Existen dos términos clave:
        - **Entrada**: Trama que ingresa al switch a través de una interfaz.
        - **Salida**: Trama que sale del switch a través de una interfaz.
    
    - Tabla de Direcciones MAC:
        Los switches mantienen una tabla de direcciones MAC (también conocida como tabla CAM) que asocia las direcciones MAC con los puertos del switch. Esta tabla es fundamental para el proceso de conmutación de tramas.

    - Proceso de Aprendizaje:
        Cuando un switch recibe una trama, aprende la dirección MAC de origen y el puerto por donde ingresó.

    - Reenvío de Tramas:
        - Si la dirección MAC de destino está en la tabla, la trama se reenvía al puerto correspondiente.
        - Si no está en la tabla, la trama se envía a todos los puertos excepto el de entrada (flooding).

```mermaid
graph TD
    A[Trama Entrante] -->|Verificar MAC de Origen| B[Actualizar Tabla MAC]
    A -->|Verificar MAC de Destino| C{¿MAC en Tabla?}
    C -->|Sí| D[Reenvío por Puerto Específico]
    C -->|No| E[Envío a Todos los Puertos Excepto el de Entrada]
```

2. **Métodos de Reenvío de un Switch**
    - **Conmutación de Almacenamiento y Reenvío (Store-and-Forward)**:
        - El switch recibe la trama completa antes de reenviarla.
        - Verifica errores CRC en la secuencia de comprobación de tramas (FCS).
        - **Ventaja**: Mayor precisión al eliminar tramas dañadas.
        - **Desventaja**: Mayor latencia comparada con otros métodos.

    - **Conmutación de Corte (Cut-through Switching)**:
        - Reenvía la trama tan pronto como se lee la dirección MAC de destino.
        - No verifica errores CRC, lo que puede propagar errores.
        - **Ventaja**: Baja latencia, ideal para aplicaciones sensibles al tiempo.
        - **Desventaja**: Puede generar problemas de ancho de banda y propagar tramas corruptas.

```mermaid
graph LR
    A[Métodos de Conmutación] -->|Store-and-Forward| B[Verifica Errores CRC]
    A -->|Cut-through| C[Reenvío Inmediato]
    B --> D[Mayor Precisión, Mayor Latencia]
    C --> E[Menor Latencia Posible, Propagación de Errores]
```

3. **Dominios de Switching**
    - **Dominios de Colisión**:
        Se producen en segmentos de red donde dos o más dispositivos compiten por el mismo ancho de banda.
        Los switches eliminan los dominios de colisión al operar en modo dúplex completo. Sin embargo, si hay dispositivos en modo semidúplex, los dominios de colisión persisten.

    - **Dominios de Difusión (Broadcast Domains)**:
        Un dominio de difusión abarca todos los dispositivos conectados a una LAN de Capa 2. Un switch inundará todas las interfaces con una trama de difusión excepto la interfaz de entrada.
        Los dominios de difusión solo se pueden segmentar con dispositivos de Capa 3 (routers).

```mermaid
graph TD
    A[Switch] -->|Dominios de Colisión Eliminados| B[Modo Dúplex Completo]
    A -->|Dominios de Colisión Persisten| C[Modo Semidúplex]
    A -->|Inunda Difusión| D[Dominios de Difusión]
    D -->|Segmentación| E[Router Capa 3]
```

4. **Técnicas de Mejora del Rendimiento de Red**
    - **Alivio de la Congestión en la Red**:
        - **Velocidades de Puertos Rápidos**: Los switches pueden soportar velocidades de puerto de hasta 100 Gbps.
        - **Switching Interno Rápido**: Uso de bus interno rápido o memoria compartida para mejorar el rendimiento.
        - **Búferes para Tramas Grandes**: Permiten el almacenamiento temporal de tramas para manejar grandes cantidades de tráfico.
        - **Alta Densidad de Puertos**: Proporciona conectividad para múltiples dispositivos en una LAN, reduciendo la congestión y costos.

```mermaid
graph TD
    A[Switch] -->|Velocidades de Puertos Rápidos| B[Hasta 100 Gbps]
    A -->|Switching Interno Rápido| C[Bus Interno Rápido]
    A -->|Búferes para Tramas Grandes| D[Almacenamiento Temporal]
    A -->|Alta Densidad de Puertos| E[Reducción de Costos y Congestión]
```

### Conclusión
Este documento cubre los conceptos esenciales de la conmutación en redes, incluyendo cómo funcionan los switches a nivel de Capa 2, los métodos de conmutación, los dominios de colisión y difusión, y las técnicas para mejorar el rendimiento de la red. Proporciona una base sólida para responder a las preguntas de retroalimentación de manera efectiva y precisa.
