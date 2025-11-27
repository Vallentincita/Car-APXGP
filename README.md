# Car-APXGP
<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/206e9634-aceb-4a1b-8383-e0cc33c6da73" />

---

## Descripción del proyecto

Este repositorio contiene el diseño completo del sistema de telemetría inalámbrica y control remoto desarrollado para el vehículo RC APXGP, como parte del RC Cars Telemetry Challenge 2025. El sistema utiliza microcontroladores Raspberry Pi Pico 2W, transceptores nRF24L01, sensores obligatorios, PCBs personalizadas y una aplicación de telemetría en PC que muestra los datos del carro en tiempo real. El proyecto cumple todos los requisitos del curso, integrando conceptos de comunicaciones digitales, modulación digital, protocolos, enlace RF, diseño electrónico, procesamiento de señales y análisis de datos.

---

# Arquitectura general del sistema

El sistema está compuesto por cuatro módulos principales, cada uno diseñado con un PCB propio:

<img width="1920" height="1080" alt="El texto del párrafo" src="https://github.com/user-attachments/assets/06fdd54b-efca-48d6-aab9-8816f2ad3af1" />

## Módulo de Sensores (Carro)
Ubicado en el vehículo, incluye:

- MPU6050 – IMU (I2C)  
- GPS NEO-6M (UART)  
- INA225 – medición de voltaje/corriente  
- LM35 – temperatura del motor  
- TCRT5000 – sensor de línea  
- nRF24L01 – canal de telemetría  
- Raspberry Pi Pico 2W – adquisición y empaquetamiento  

Encargado de transmitir telemetría en tiempo real al puesto de recepción.

---

## Módulo de Actuadores (Carro)
Recibe las órdenes del piloto mediante un segundo enlace RF:

- Control del servomotor (PWM)  
- Control del ESC del motor  
- Parada de emergencia (E-Stop)  
- Validación y decodificación de paquetes  
- Gestión de alimentación del tren motriz  

---

## Control Remoto
Diseñado sobre una PCB ergonómica:

- 2 joysticks analógicos  
- Pantalla OLED  
- Botón E-Stop  
- Pico 2W  
- nRF24L01 dedicado al enlace de control  

Envía paquetes digitales continuamente con dirección, velocidad y estado del sistema.

---

## Puesto de Recepción (Gateway RF → USB)
Opera como puente entre el enlace RF y la aplicación en PC:

- Pico 2W  
- nRF24L01  
- Interfaz USB/CDC  
- Decodificación y envío continuo al software de telemetría  

---

# Enlaces inalámbricos

El sistema trabaja con dos canales independientes:

- **Canal A:** Control → Carro  
- **Canal B:** Telemetría → Puesto de recepción

---

# Aplicación de Telemetría en PC

Desarrollada para visualizar los datos en tiempo real:

- Gráfico de acelerómetro 3 ejes (IMU)  
- Temperatura del motor  
- Voltaje y estado de batería  
- Mapa GPS del carro  
- Valores PWM (motor y servo)  
- Estado del enlace RF  
- Registro automático en CSV

El sistema permite análisis posterior de carrera, comparación de vueltas y diagnóstico del vehículo.

---

# Mediciones de laboratorio

El diseño fue validado con:

- **Osciloscopio** → Señal PWM de servomotor  
- **Analizador lógico** → Comunicación SPI entre Pico y nRF24L01  
- **Analizador de espectros** → Canal RF, potencia (~–85 dBm), coexistencia con Wi-Fi  

Estas mediciones comprobaron estabilidad y correcta configuración del enlace.

---

# Diagramas técnicos incluidos

El repositorio contiene los diagramas completos del proyecto:

- Diagramas de bloques  
- Esquemáticos electrónicos de cada PCB  
- Layouts PCB y vistas 3D  
- Diagramas de flujo del firmware  
- UML:  
  - Casos de uso  
  - Clases  
  - Secuencias del enlace control/telemetría  

---

# Fotografías del sistema (colocar aquí)

### Carro completo  
<img width="1280" height="960" alt="image" src="https://github.com/user-attachments/assets/62e29e44-6b2c-4b0a-9f9c-294cce091076" />

### Control remoto  
<img width="1600" height="1201" alt="image" src="https://github.com/user-attachments/assets/02ac550a-7589-45b0-8fec-1f5951ab0c1f" />

### PCB sensores  
<img width="1280" height="960" alt="image" src="https://github.com/user-attachments/assets/34957b9f-1079-4559-b2ba-0d02ed825210" />

### PCB receptor  
<img width="1600" height="1201" alt="image" src="https://github.com/user-attachments/assets/c5af62ab-3753-4c7e-ae61-5e92b0bfc14a" />

---

Autores

Vallentina Diaz Valbuena 
Juan Esteban Mora Vaca  
Luis Carlos Leal Gamboa  
Brayan Steven Mendivelso Perez

Docente: José de Jesús Rugeles

---

Este proyecto es de carácter académico para el curso de Comunicaciones Digitales — UMNG.
