## Hi there 👋
# Control de Barra de LEDs con Raspberry Pi Pico W y Servidor Web

Este proyecto utiliza una Raspberry Pi Pico W para controlar una barra de 8 LEDs mediante un servidor web. El usuario puede seleccionar diferentes patrones de luces desde una página web simple, accesible desde cualquier dispositivo conectado a la misma red Wi-Fi.

## Funcionalidad

El código consta de dos partes principales:

1.  **Código Python para la Pico W (`pico.py`)**:
    * Configura la Pico W como un punto de acceso Wi-Fi (modo AP) o se conecta a una red existente (modo STA).
    * Controla los 8 LEDs conectados a los pines GPIO 2 a 9.
    * Ejecuta varios patrones de luz predefinidos, como secuencias, efectos de vúmetro y estroboscópicos.
    * Crea un servidor web HTTP que sirve una página HTML (`INDEX_HTML`) y procesa las peticiones de los botones.

2.  **Página Web (`INDEX_HTML`)**:
    * Una interfaz de usuario simple con una cuadrícula de 9 botones.
    * Cada botón envía una petición `GET` a la Pico W con un parámetro de "tecla" (`k=1`, `k=2`, etc.).
    * Utiliza JavaScript para enviar las peticiones al servidor y mostrar el estado de la operación.

## Requisitos de Hardware

* **Raspberry Pi Pico W**
* **Barra de 8 LEDs con conexión de cátodo común** (o 8 LEDs individuales y resistencias)
* Cables de conexión (jumpers)

## Configuración y Ejecución

Para ejecutar este proyecto, sigue los siguientes pasos:

1.  **Software**: Asegúrate de tener **MicroPython** instalado en tu Raspberry Pi Pico W. Puedes usar herramientas como Thonny IDE para subir el código.

2.  **Cableado**: Conecta los 8 LEDs a los pines GPIO de la Pico W según la siguiente configuración:
    * LED 1 -> GPIO 2
    * LED 2 -> GPIO 3
    * ...
    * LED 8 -> GPIO 9
    * Conecta el polo común de los LEDs a tierra (GND) en la Pico W.

3.  **Configuración del Código (`pico.py`)**:
    * Modifica las variables **`AP_SSID`** y **`AP_PASSWORD`** en el archivo `pico.py` para definir el nombre y la contraseña de la red Wi-Fi que creará la Pico.
    * Si prefieres que la Pico se conecte a tu red Wi-Fi doméstica, cambia **`MODO_STA = True`** y descomenta y configura tu **`SSID`** y **`PASSWORD`**.

4.  **Subir el Código**:
    * Guarda el archivo `pico.py` en tu computadora.
    * Utiliza Thonny u otro IDE compatible con MicroPython para subir el archivo `pico.py` a la Raspberry Pi Pico W.

5.  **Acceder al Servidor Web**:
    * Una vez que el código esté corriendo, la Pico W encenderá un LED (usualmente el integrado) y se conectará o creará la red.
    * Abre la consola de Thonny y anota la dirección IP que se imprime (por ejemplo: `Server at http://192.168.4.1`).
    * Conecta un teléfono o computadora a la red Wi-Fi creada por la Pico W y navega a la dirección IP en un navegador web para controlar los LEDs.

## Desafíos y Soluciones

* **Problemas de conexión Wi-Fi**: Inicialmente, hubo dificultades para la Pico W para conectarse a algunas redes Wi-Fi de 5 GHz. La solución fue asegurar el uso de la banda de 2.4 GHz y, en el modo AP, garantizar que la contraseña tuviera al menos 8 caracteres.
* **Control de los LEDs con la red**: El desafío fue lograr que la Pico W pudiera escuchar peticiones HTTP mientras ejecutaba los patrones de luz. La solución fue usar un servidor web simple que procesa las peticiones de forma rápida y luego llama a las funciones de los patrones.
* **HTML y HTTP**: Hubo que manejar la complejidad de servir una página web y procesar peticiones `GET` con parámetros en un entorno de microcontrolador. La función `http_send()` se creó para estandarizar las respuestas HTTP y la lógica en `serve()` para analizar las peticiones entrantes.

## Autor

* **Erik Chavez Avalos** 
Microprocesadores
<!--
**theweeriknd/theweeriknd** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
