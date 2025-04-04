# Examen de Redes II  

---

# Parte I: Conceptos y Teoría

---

## Pregunta 1: El Mural de las Siete Capas

**¿Qué representa el mural de las siete capas en términos de las redes de comunicación modernas? Identifica brevemente cada capa y explica cómo se relaciona este antiguo “modelo” con el proceso de comunicación de datos actual.**

El mural de las siete capas es una representación del Modelo OSI (Open Systems Interconnection), un marco conceptual que divide el proceso de comunicación en redes en siete capas distintas. Este modelo es fundamental para entender cómo se estandariza la comunicación entre diferentes sistemas y tecnologías en el ámbito de las redes modernas. A continuación, se describen brevemente cada una de las capas y su relación con el proceso de comunicación de datos actual.

| Capa | Nombre             | Función principal                                                              |
|------|--------------------|--------------------------------------------------------------------------------|
| 1    | Física             | Transmisión de bits a través del medio físico.                                |
| 2    | Enlace de Datos    | Control de acceso al medio, detección/corrección de errores, direcciones MAC. |
| 3    | Red                | Enrutamiento de paquetes entre redes (ej. IP).                                |
| 4    | Transporte         | Segmentación, control de flujo, fiabilidad (TCP/UDP).                         |
| 5    | Sesión             | Establecimiento, gestión y terminación de sesiones.                           |
| 6    | Presentación       | Formato, compresión y cifrado de datos.                                       |
| 7    | Aplicación         | Interfaz entre usuario y red (ej. HTTP, FTP, DNS).                            |


![Interpretación moderna_ Las 7 capas del Modelo OSI - visual selection](https://github.com/user-attachments/assets/376fdb0a-9c46-481b-b6a0-111c10c8c3e8)

---

## Pregunta 2: Los Dos Pergaminos del Mensajero

**¿A qué protocolos de comunicación actuales equivalen el mensajero confiable y el mensajero veloz? Compara sus características, explicando las ventajas y desventajas de cada enfoque en redes modernas.**

- **Mensajero confiable**: equivale a **TCP (Transmission Control Protocol)**  
- **Mensajero veloz**: equivale a **UDP (User Datagram Protocol)**

| Característica        | TCP                                  | UDP                               |
|-----------------------|---------------------------------------|-----------------------------------|
| Tipo de conexión      | Orientado a conexión                  | No orientado a conexión           |
| Fiabilidad            | Alta (uso de ACK, control de errores) | Baja                              |
| Orden de entrega      | Garantizado                           | No garantizado                    |
| Velocidad             | Menor                                 | Mayor                             |
| Aplicaciones típicas  | Web, email, FTP, SSH                  | Streaming, VoIP, juegos online    |

Ventajas y Desventajas

#### Ventajas de TCP

Fiabilidad en la entrega: TCP asegura que los datos lleguen correctamente al destino mediante el uso de acuses de recibo (ACK) y mecanismos de control de errores. Esto es crucial para aplicaciones donde la integridad de los datos es fundamental, como en la transferencia de archivos o en correos electrónicos.

#### Desventajas de TCP

Mayor sobrecarga y latencia: Debido a sus características de fiabilidad y control, TCP introduce una mayor sobrecarga en la red, lo que puede resultar en latencias más altas. Esto puede ser un inconveniente en aplicaciones que requieren una respuesta rápida.

#### Ventajas de UDP

Bajo retardo: UDP permite una transmisión más rápida de datos al no requerir la confirmación de entrega ni el control de errores. Esto lo hace ideal para aplicaciones en tiempo real como streaming de video, VoIP y juegos en línea, donde la velocidad es más crítica que la fiabilidad.

#### Desventajas de UDP

No garantiza entrega ni orden: A diferencia de TCP, UDP no asegura que los paquetes lleguen a su destino ni que lo hagan en el orden correcto. Esto puede ser problemático en aplicaciones donde la secuenciación de los datos es importante.

![Comparación de Protocolos de Comunicación_ TCP y UDP - visual selection](https://github.com/user-attachments/assets/0c47532b-f9cd-4dcd-9e92-2c3d48056682)


---

## Pregunta 3: El Enigma de las Subredes

**Si la antigua red usaba la dirección 192.168.50.0 como base y necesitaba dividirse en 4 subredes de igual tamaño, ¿qué máscara de subred habrían utilizado los antiguos para lograrlo? ¿Cuántas direcciones de host (utilizables) tendría cada subred resultante?**

- Red base: `192.168.50.0/24`  
- Se requieren 4 subredes → se usan 2 bits más → nueva máscara: **/26**  
- Cada subred /26 tiene: 2⁶ - 2 = **62 hosts utilizables**

| Subred | Rango IP                  | Hosts utilizables |
|--------|---------------------------|-------------------|
| 1      | 192.168.50.0 – 63         | 62                |
| 2      | 192.168.50.64 – 127       | 62                |
| 3      | 192.168.50.128 – 191      | 62                |
| 4      | 192.168.50.192 – 255      | 62                |

**Máscara utilizada:** `255.255.255.192` (**/26**)

---

## Pregunta 4: La Encrucijada de las Rutas

**¿Qué concepto moderno de redes representa el tótem con flechas de la encrucijada? Explica qué es una tabla de enrutamiento y cómo funciona en un router actual. Además, interpreta la diferencia entre las flechas talladas en piedra y las flechas móviles en términos de enrutamiento estático vs. enrutamiento dinámico en redes.**

#### Tabla de Enrutamiento

- Una tabla de enrutamiento es una estructura fundamental en el funcionamiento de los routers. Esta tabla contiene rutas que indican al router por qué interfaz debe enviar un paquete de datos, dependiendo de su dirección IP de destino. La correcta configuración y mantenimiento de esta tabla son esenciales para garantizar que los datos se transmitan de manera eficiente y efectiva a través de una red.


| Tipo de enrutamiento | Descripción                               |
|----------------------|--------------------------------------------|
| Estático             | Rutas configuradas manualmente. Estables. |
| Dinámico             | Rutas aprendidas automáticamente (RIP, OSPF). Se actualizan ante cambios. |

#### Enrutamiento Estático vs Enrutamiento Dinámico

-**Flechas talladas en piedra:** Representan el enrutamiento estático, donde las rutas son configuradas manualmente por un administrador de red. Estas rutas son estables y no cambian a menos que se realice una intervención manual. Esto puede ser beneficioso en entornos donde las rutas son predecibles y no cambian con frecuencia.

-**Flechas móviles:** Simbolizan el enrutamiento dinámico, donde las rutas son aprendidas automáticamente por el router a través de protocolos de enrutamiento como RIP (Routing Information Protocol) o OSPF (Open Shortest Path First). Estas rutas se actualizan automáticamente en respuesta a cambios en la topología de la red, lo que permite una mayor flexibilidad y adaptabilidad en entornos de red más complejos.

![La Encrucijada de las Rutas_ Un Análisis del Enrutamiento en Redes Modernas - visual selection](https://github.com/user-attachments/assets/0bb8efd5-f347-4cb9-829f-5998a0eb8dac)

---

## Pregunta 5: El Guardián de la Máscara Única

**¿Qué técnica de redes moderna se refleja en la leyenda del Guardián de la Máscara? Nombra y describe brevemente este mecanismo, explicando cómo permite que múltiples dispositivos internos de una red compartan una única identidad (dirección) al comunicarse con el exterior, y menciona dos beneficios que brinda esta estrategia a las redes actuales.**

La técnica es **NAT (Network Address Translation)**.

### Descripción:
- NAT permite que múltiples dispositivos en una red privada (ej. 192.168.x.x) compartan una sola dirección IP pública al acceder a Internet.
- El router reemplaza la IP privada con su IP pública al salir y mantiene una tabla para redirigir las respuestas al host correspondiente.

### Beneficios:
1. **Conservación de direcciones IPv4 públicas**
2. **Ocultamiento de la red interna, mejorando la seguridad**




