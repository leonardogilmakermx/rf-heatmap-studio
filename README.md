# RF Heatmap Studio Enterprise 2D / 3D

[![Licencia](https://img.shields.io/badge/Licencia-Propietaria%20%2F%20Todos%20los%20derechos%20reservados-0891b2.svg)](LICENSE)
[![Estándares Wi-Fi](https://img.shields.io/badge/Wi--Fi-5%20%7C%206%20%7C%207%20(802.11ac%2Fax%2Fbe)-10b981.svg)]()
[![Tecnologías](https://img.shields.io/badge/Three.js-WebGL%203D-blue.svg)]()
[![Plataforma](https://img.shields.io/badge/Plataforma-Web%20%2F%20Cero%20Instalación-cyan.svg)]()

> **Diseñado y desarrollado por el Ing. G. Leonardo Dominguez Garcia.**  
> Plataforma web integral para la simulación precisa de propagación electromagnética de radiofrecuencia (RF), mapas de calor predictivos bidimensionales y tridimensionales, modelado de atenuación estructural y análisis de espectro en tiempo real.

---

## 📌 Descripción General

**RF Heatmap Studio Enterprise** es una solución de ingeniería en telecomunicaciones diseñada para planificar, evaluar y auditar infraestructuras de red inalámbrica sin necesidad de software costoso ni instalaciones complejas en el sistema operativo.

La aplicación permite posicionar múltiples Puntos de Acceso (APs), modelar muros con coeficientes de pérdida de penetración en decibeles (dB), calibrar escalas métricas reales sobre planos arquitectónicos y simular el enlace con dispositivos móviles (STAs) bajo los estándares **Wi-Fi 5 (802.11ac)**, **Wi-Fi 6 (802.11ax)** y **Wi-Fi 7 (802.11be)**.

---

## 🚀 Características Principales

### 📡 1. Arquitectura Multi-AP y Modelado de Antenas
- **Soporte de Bandas:** Configuración independiente por AP en **2.4 GHz**, **5.0 GHz** y **6.0 GHz (Wi-Fi 6E/7)**.
- **Patrones de Radiación de Antena:**
  - **Omnidireccional (360°):** Cobertura circular estándar.
  - **Direccional / Sectorial (Patch):** Apertura de haz a media potencia (HPBW) seleccionable en **30°, 45°, 60° y 90°**, con orientación de azimut de **0° a 360°**, ganancia pico en dBi y atenuación posterior (*Front-to-Back ratio*).
- **Control de Transmisión:** Regulación de potencia radiada aparente (EIRP en dBm) y altura física de instalación ($Z$).

### 🧱 2. Modelado Arquitectónico y Atenuación de Materiales
- **Herramienta de Trazo Interactivo:** Dibuja muros libremente con cálculo continuo de longitud euclidiana y altura métrica.
- **Catálogo de Materiales con Factor de Frecuencia:**
  - Tablaroca / Drywall ($3.0\text{ dB}$)
  - Vidrio arquitectónico ($2.5\text{ dB}$)
  - Ladrillo estándar ($6.0\text{ dB}$)
  - Concreto armado / Muros estructurales ($15.0\text{ dB}$)
  - Metal y blindajes electromagnéticos ($28.0\text{ dB}$)
  - Atenuación personalizada por muro o sector.
- **Calibración Métrica:** Herramienta de regla para fijar la escala metros/píxeles a partir de una cota conocida del plano.

### 📱 3. Emulación de Clientes (STAs) y Roaming Dinámico
- **Categorías de Dispositivo:** Smartphones, Laptops, Tablets y Sensores IoT con ganancias de antena diferenciadas.
- **Roaming Autónomo:** Evaluación matricial continua de la mejor relación señal/ruido e interferencia (**SINR**) para conmutación de AP.
- **Telemetría de Enlace en Vivo:** Distancia 2D/3D exacta ($d$), atenuación acumulada por muros intermedios, RSSI en dBm y tasa de transferencia proyectada (Throughput en Mbps).

### ⚡ 4. Agentes de Ruido e Interferencia No-WiFi
- Simulación de fuentes de interferencia electromagnética comunes:
  - Hornos de microondas (fuga de magnetrón en $2.45\text{ GHz}$)
  - Altavoces y dispositivos Bluetooth (FHSS)
  - Luminarias LED con balastras de conmutación no apantalladas (*Broadband EMI*)
  - Compresores de aire acondicionado / HVAC inverter
  - Radares Doppler e instrumentación en $5.8\text{ GHz}$
- Cálculo de elevación del piso de ruido térmico y colapso de la modulación MCS.

### 📊 5. Analizador de Espectro RF Integrado
- Vista espectral en el receptor para cada dispositivo cliente seleccionado.
- Densidad espectral de potencia (PSD) con máscaras de canal OFDM/OFDMA para 20, 40, 80, 160 y 320 MHz.
- Diagnóstico de solapamiento de canal (CCI/ACI) y recomendación de frecuencias óptimas.

### 🧊 6. Visualización 3D con Three.js
- Extrusión volumétrica de muros en base a su altura real en metros.
- Proyección del mapa de calor directo sobre el plano arquitectónico.
- Haces de radiofrecuencia volumétricos tridimensionales conectando APs y dispositivos.
- Representación tridimensional de los lóbulos de radiación de antenas direccionales.

---

## 📐 Fundamentos Físicos y Matemáticos

### 1. Pérdida de Trayectoria en Espacio Libre (FSPL)
$$FSPL(d, f) = 20\log_{10}(d) + 20\log_{10}(f) - 27.55$$
*Donde $d$ es la distancia tridimensional en metros y $f$ es la frecuencia en MHz.*

### 2. Modelo de Atenuación por Partición de Obstáculos (Multi-Wall Model)
$$RSSI(x,y,z) = P_{tx} + G(\theta) - FSPL(d, f) - \sum_{k=1}^{M} W_k(f)$$
*Donde $W_k(f)$ representa la atenuación del muro cruzado ponderada por la frecuencia portadora.*

### 3. Patrón de Radiación de Antena Direccional (Modelo 3GPP/ITU)
$$G(\theta) = G_{\max} - \min\left(12 \cdot \left(\frac{\theta}{\theta_{3\text{dB}}}\right)^2, \; \text{F2B}\right)$$

### 4. Relación Señal a Ruido + Interferencia (SINR)
$$SINR = RSSI - 10\log_{10}\left(10^{\frac{N_0}{10}} + \sum_{j} 10^{\frac{I_j}{10}}\right)$$

---

## 🛠️ Tecnologías Empleadas

- **Lenguaje:** HTML5, CSS3, JavaScript (Vanilla ES6+).
- **Motor 3D:** [Three.js](https://threejs.org/) (r128) + OrbitControls.
- **Estilos:** [Tailwind CSS](https://tailwindcss.com/) (CDN).
- **Iconografía:** [Lucide Icons](https://lucide.dev/).
- **Arquitectura:** Aplicación en un único archivo autocontenido (*Single-File Architecture*), sin dependencias locales de Node.js o empaquetadores.

---

## 💻 Instalación y Despliegue Rápido

### Opción 1: Ejecución Local
1. Clona el repositorio o descarga el archivo:
   ```bash
   git clone https://github.com/TU-USUARIO/TU-REPOSITORIO.git
   ```
2. Renombra el archivo principal a `index.html` (o ábrelo directamente haciendo doble clic sobre `wifi_heatmap_studio.html` en cualquier navegador web moderno).

### Opción 2: Despliegue Gratuito en GitHub Pages
1. Renombra `wifi_heatmap_studio.html` a **`index.html`**.
2. Sube el archivo a la rama `main` de tu repositorio.
3. En GitHub, dirígete a: **Settings** $\rightarrow$ **Pages**.
4. En **Build and deployment** / **Branch**, selecciona `main` y guarda los cambios.
5. Tu simulador estará en línea en la URL:
   `https://TU-USUARIO.github.io/TU-REPOSITORIO/`

---

## 📜 Propiedad Intelectual y Autoría

Este software, su arquitectura de cálculo electromagnético y su sistema de visualización tridimensional fueron concebidos, diseñados y programados por:

**Ing. G. Leonardo Dominguez Garcia**  
*Arquitecto de Software & Especialista en Simulación de Radiofrecuencia (RF)*  
*Todos los derechos reservados © 2026.*

> El código fuente cuenta con mecanismos de comprobación e integridad de créditos en tiempo de ejecución.