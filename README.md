# Car-APXGP
<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/206e9634-aceb-4a1b-8383-e0cc33c6da73" />
# 🚗 RC Car APXGP — Wireless Telemetry & Control System  
### Universidad Militar Nueva Granada · Ingeniería en Telecomunicaciones  
### Proyecto final — Comunicaciones Digitales 2025

---

## 📌 Descripción del proyecto

Este repositorio contiene el diseño completo del **sistema de telemetría inalámbrica y control remoto** desarrollado para el vehículo RC **APXGP**, como parte del RC Cars Telemetry Challenge 2025.  
El sistema utiliza microcontroladores **Raspberry Pi Pico 2W**, transceptores **nRF24L01**, sensores obligatorios, PCBs personalizadas y una aplicación de telemetría en PC que muestra los datos del carro en tiempo real.

El proyecto cumple todos los requisitos del curso, integrando conceptos de comunicaciones digitales, modulación digital, protocolos, enlace RF, diseño electrónico, procesamiento de señales y análisis de datos.

---

# 🧩 Arquitectura general del sistema

El sistema está compuesto por **cuatro módulos principales**, cada uno diseñado con un PCB propio:

## 1️⃣ Módulo de Sensores (Carro)
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

## 2️⃣ Módulo de Actuadores (Carro)
Recibe las órdenes del piloto mediante un segundo enlace RF:

- Control del servomotor (PWM)  
- Control del ESC del motor  
- Parada de emergencia (E-Stop)  
- Validación y decodificación de paquetes  
- Gestión de alimentación del tren motriz  

---

## 3️⃣ Control Remoto
Diseñado sobre una PCB ergonómica:

- 2 joysticks analógicos  
- Pantalla OLED  
- Botón E-Stop  
- Pico 2W  
- nRF24L01 dedicado al enlace de control  

Envía paquetes digitales continuamente con dirección, velocidad y estado del sistema.

---

## 4️⃣ Puesto de Recepción (Gateway RF → USB)
Opera como puente entre el enlace RF y la aplicación en PC:

- Pico 2W  
- nRF24L01  
- Interfaz USB/CDC  
- Decodificación y envío continuo al software de telemetría  

---

# 🛰️ Enlaces inalámbricos

El sistema trabaja con **dos canales independientes**:

- **Canal A:** Control → Carro  
- **Canal B:** Telemetría → Puesto de recepción  

Ambos utilizan modulación **GFSK**, paquetes de 1 MHz y CRC para robustez.

---

# 🖥️ Aplicación de Telemetría en PC

Desarrollada para visualizar los datos en tiempo real:

- Gráfico de acelerómetro 3 ejes (IMU)  
- Temperatura del motor  
- Voltaje y estado de batería  
- Mapa GPS del carro  
- Valores PWM (motor y servo)  
- Estado del enlace RF  
- Registro **automático en CSV**  

El sistema permite análisis posterior de carrera, comparación de vueltas y diagnóstico del vehículo.

---

# 🔧 Mediciones de laboratorio

El diseño fue validado con:

- **Osciloscopio** → Señal PWM de servomotor  
- **Analizador lógico** → Comunicación SPI entre Pico y nRF24L01  
- **Analizador de espectros** → Canal RF, potencia (~–85 dBm), coexistencia con Wi-Fi  

Estas mediciones comprobaron estabilidad y correcta configuración del enlace.

---

# 📐 Diagramas técnicos incluidos

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

# 📸 Fotografías del sistema (colocar aquí)

Agrega tus imágenes en `/media/` y enlázalas aquí:

### Carro completo  
![Carro APXGP](media/carro_completo.jpg)

### Control remoto  
![Control](media/control.jpg)

### PCB sensores  
![PCB Sensores](media/pcb_sensores.jpg)

### PCB receptor  
![PCB Receptor](media/pcb_receptor.jpg)

---

# 🛠️ Cómo ejecutar la aplicación

### 1. Conectar el puesto de recepción vía USB  
El dispositivo enviará líneas de telemetría por puerto serial.

### 2. Ejecutar la aplicación en PC  
(Agregar instrucciones dependiendo de tu lenguaje: Python, C#, Java, etc.)

Ejemplo Python:
```bash
python app_telemetria.py
```

### 3. Iniciar el carro  
La telemetría comenzará a recibirse y graficarse automáticamente.

---

# 📂 Estructura del repositorio

```
Car-APXGP/
│
├── docs/               → Informe técnico y diagramas
├── hardware/           → PCB, esquemáticos, Gerbers
├── media/              → Fotos, capturas y videos
├── data/               → CSV generados por la telemetría
├── firmware/           → Código del carro, control y receptor
├── pc_app/             → Aplicación de telemetría en PC
└── README.md           → Este archivo
```

---

# 🤖 Proceso de diseño asistido por IA

Este proyecto integró herramientas de IA (ChatGPT, Cursor, GitHub Copilot, Perplexity) para:

- refactorización de código en MicroPython  
- documentación técnica  
- análisis de problemas de RF  
- corrección del flujo SPI  
- generación de diagramas conceptuales  

Todas las decisiones finales fueron verificadas mediante pruebas físicas.

---

# 👥 Autores

**Vallentina Diaz Valbuena**  
**Juan Esteban Mora Vaca**  
**Luis Carlos Leal Gamboa**  
**Brayan Steven Mendivelso Perez**

Docente: **José de Jesús Rugeles**

---

# 📄 Licencia

Este proyecto es de carácter académico para el curso de Comunicaciones Digitales — UMNG.
