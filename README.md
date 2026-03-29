# 🤖 Prototipo de Robot móvil Cortacésped

Este repositorio contiene el diseño de hardware y el firmware base para la unidad de control central de un robot móvil cortacésped teleoperado

El núcleo de este proyecto es una **PCB personalizada**  diseñada para gestionar potencia, navegación y sistema de seguridad utilizando el microcontrolador **ESP32-S3**.

## Especificaciones Técnicas de la PCB

Nuestra especialización se centra en la integración de sensores y la gestión de actuadores de potencia:

### Cerebro y Conectividad
* **MCU:** `ESP32-S3-WROOM-1`. Doble núcleo con soporte nativo para Wi-Fi y Bluetooth

### Sistema de Seguridad y Detección de Obstáculos
El robot implementa una estrategia de seguridad de dos niveles:
1.  **Nivel Preventivo (Ultrasonidos):** 3 sensores ultrasónicos estratégicamente posicionados para la detección de obstáculos a distancia
2.  **Nivel de Contacto (Bumpers):** 4 finales de carrera instalados en el chasis como "Bumpers". Funcionan como la última barrera física
* **Regulación:** `LDL1117S33R`. LDO de alta eficiencia para una alimentación estable de 3.3V.
* **Precisión de Batería:** `ADS1015LIDGSR`. ADC externo de 12 bits para un monitoreo crítico del voltaje

### Navegación y Movimiento
* **IMU:** `IIM-42652`. Sensor de 6 ejes de grado industrial para mantener el rumbo y detectar inclinaciones peligrosas.
* **Control de Tracción:** Pines de salida (Dupont) para conectar un **driver de motor DC externo** para el desplazamiento del robot.

### Sistema de Corte (Brushless)
La PCB cuenta con salidas específicas para controlar **3 ESC (Electronic Speed Controllers)** independientes:
* **2 Motores Brushless:** Dedicados al corte principal de césped.
* **1 Motor Brushless:** Dedicado a la función de bordeadora

### Interfaz de Usuario
* **Buzzer SMT:** `CMI-9705-0580-SMT-TR`. Notifica mediante códigos acústicos:
    * **Movimiento inminente:** Alerta antes de activar cuchillas o tracción.
    * **Batería Baja:** Alerta de retorno a base.
