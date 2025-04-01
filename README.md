# Examen de Redes II – Parte I: Conceptos y Teoría

---

## Pregunta 1: El Mural de las Siete Capas

**¿Qué representa el mural de las siete capas en términos de las redes de comunicación modernas? Identifica brevemente cada capa y explica cómo se relaciona este antiguo “modelo” con el proceso de comunicación de datos actual.**

El mural representa el **Modelo OSI (Open Systems Interconnection)**, que divide el proceso de comunicación en redes en 7 capas. Cada capa tiene funciones específicas que ayudan a estandarizar la comunicación entre sistemas.

| Capa | Nombre             | Función principal                                                              |
|------|--------------------|--------------------------------------------------------------------------------|
| 1    | Física             | Transmisión de bits a través del medio físico.                                |
| 2    | Enlace de Datos    | Control de acceso al medio, detección/corrección de errores, direcciones MAC. |
| 3    | Red                | Enrutamiento de paquetes entre redes (ej. IP).                                |
| 4    | Transporte         | Segmentación, control de flujo, fiabilidad (TCP/UDP).                         |
| 5    | Sesión             | Establecimiento, gestión y terminación de sesiones.                           |
| 6    | Presentación       | Formato, compresión y cifrado de datos.                                       |
| 7    | Aplicación         | Interfaz entre usuario y red (ej. HTTP, FTP, DNS).                            |

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

- **Ventaja de TCP**: Fiabilidad en la entrega.  
- **Desventaja de TCP**: Mayor sobrecarga y latencia.  
- **Ventaja de UDP**: Bajo retardo, ideal para tiempo real.  
- **Desventaja de UDP**: No garantiza entrega ni orden.

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

El tótem representa una **tabla de enrutamiento**.

- Una **tabla de enrutamiento** contiene rutas que indican al router por qué interfaz enviar un paquete según su destino IP.

| Tipo de enrutamiento | Descripción                               |
|----------------------|--------------------------------------------|
| Estático             | Rutas configuradas manualmente. Estables. |
| Dinámico             | Rutas aprendidas automáticamente (RIP, OSPF). Se actualizan ante cambios. |

- **Flechas talladas en piedra** → Rutas estáticas  
- **Flechas móviles** → Rutas dinámicas

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

![Interpretación moderna_ Las 7 capas del Modelo OSI - visual selection](https://github.com/user-attachments/assets/376fdb0a-9c46-481b-b6a0-111c10c8c3e8)




