# 🚦 Semáforo Inteligente Interactivo - Vue 3 + Vite

![Banner del Semáforo Inteligente](./public/banner.png)

Este es un simulador interactivo y moderno de un semáforo de tránsito desarrollado en **Vue 3** utilizando la **Composition API (`<script setup>`)** y **Vite**. Cuenta con un diseño premium *glassmórfico*, controles avanzados, registro de eventos en tiempo real y estadísticas del sistema.

---

## ✨ Características Principales

*   **🎨 Diseño Premium**: Interfaz moderna con fondos oscuros, gradientes armoniosos y efectos de iluminación LED/neón realistas para cada estado del semáforo.
*   **⚙️ Configuración Dinámica (Props)**: Ajusta la duración en segundos de cada color (Verde, Amarillo y Rojo) de manera independiente desde el panel de control.
*   **🕹️ Modo Interactivo**: Permite forzar el cambio de color haciendo **clic directo** sobre cada una de las luces físicas del semáforo.
*   **📊 Estadísticas de Tráfico**:
    *   **Ciclos Completos**: Contador automático de ciclos de tráfico completados (transición completa de Rojo de vuelta a Verde).
    *   **Tiempo Simulado**: Cronómetro acumulativo de los segundos transcurridos con la simulación en marcha.
*   **📝 Registro en Tiempo Real (Logs)**: Historial detallado de todas las acciones del sistema (inicios, pausas, reinicios, transiciones automáticas y cambios manuales) con marcas de tiempo detalladas y colores asociados al evento.

---

## 🛠️ Arquitectura de Componentes

La aplicación está modularizada para facilitar su mantenimiento y escalabilidad:

### 1. [App.vue](file:///c:/Users/LUIS%20ANGEL/OneDrive/semaforo/src/App.vue) (Componente Dashboard)
Funciona como el orquestador principal. Gestiona el estado de la simulación, acumula estadísticas, recopila y muestra el historial de eventos en tiempo real, y proporciona el panel de control para ajustar la configuración de tiempos. Su diseño visual y componentes responsivos están definidos en [style.css](file:///c:/Users/LUIS%20ANGEL/OneDrive/semaforo/src/style.css).

### 2. [TrafficLight.vue](file:///c:/Users/LUIS%20ANGEL/OneDrive/semaforo/src/components/TrafficLight.vue) (Componente Semáforo)
Representa la estructura física del semáforo y su lógica temporal interna. Se conecta como componente hijo en la interfaz. Recibe configuraciones a través de **Props** y notifica cambios de estado y ticks mediante **Emits**.

### 3. [main.js](file:///c:/Users/LUIS%20ANGEL/OneDrive/semaforo/src/main.js) (Punto de Entrada)
El archivo principal de JavaScript que inicializa la aplicación Vue 3, importa los estilos globales de [style.css](file:///c:/Users/LUIS%20ANGEL/OneDrive/semaforo/src/style.css) y monta el componente principal [App.vue](file:///c:/Users/LUIS%20ANGEL/OneDrive/semaforo/src/App.vue) en el contenedor `#app` de [index.html](file:///c:/Users/LUIS%20ANGEL/OneDrive/semaforo/index.html).

### 4. [index.html](file:///c:/Users/LUIS%20ANGEL/OneDrive/semaforo/index.html) (Contenedor HTML)
Punto de entrada de la aplicación web que contiene la estructura HTML básica, vincula las tipografías de Google Fonts (Inter y Orbitron) y define el contenedor `#app` para montar la aplicación Vue.

#### 🔌 Especificación de Comunicación (Props y Emits)

*   **Props**:
    *   `durations`: Objeto con las duraciones `{ green, yellow, red }` de cada color.
    *   `isRunning`: Booleano para pausar/reanudar el flujo temporal.
    *   `resetToken`: Token numérico que al cambiar reinicia el semáforo al estado inicial.
*   **Emits**:
    *   `tick`: Emite `{ color, timeLeft }` cada segundo.
    *   `color-change`: Emite `{ from, to, duration, forced }` al cambiar de color.

---

## 🚀 Guía de Inicio Rápido

### Requisitos Previos

*   [Node.js](https://nodejs.org/) (versión 18 o superior recomendada).
*   Un gestor de paquetes como `npm` (incluido con Node.js).

### Instalación

1. Clona o abre el directorio del proyecto:
   ```bash
   cd semaforo
   ```

2. Instala las dependencias necesarias:
   ```bash
   npm install
   ```

### Desarrollo

Para iniciar el servidor de desarrollo local con recarga rápida (HMR):

```bash
npm run dev
```

El servidor estará listo en `http://localhost:5173/`.

### Producción

Para construir y optimizar el proyecto para producción:

```bash
npm run build
```

Los archivos finales optimizados se generarán en la carpeta `dist/`.
