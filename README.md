# Sistema de Asistencia Basado en el Reconocimiento Facial

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![OpenCV](https://img.shields.io/badge/OpenCV-Enabled-brightgreen.svg)
![Face Recognition](https://img.shields.io/badge/Face_Recognition-Used-orange.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg) ## 📜 Tabla de Contenidos

* [Introducción](#-introducción)
* [Problema y Motivación](#-problema-y-motivación)
* [Características](#-características)
* [Tecnologías Utilizadas](#-tecnologías-utilizadas)
* [Instalación](#-instalación)
    * [Requisitos Previos](#requisitos-previos)
    * [Pasos de Instalación](#pasos-de-instalación)
* [Uso](#-uso)
    * [Paso 1: Preparar las Imágenes de Rostros Conocidos](#paso-1-preparar-las-imágenes-de-rostros-conocidos)
    * [Paso 2: Ejecutar el Sistema](#paso-2-ejecutar-el-sistema)
* [Registro de Asistencia](#-registro-de-asistencia)
* [Consideraciones y Mejoras Futuras](#-consideraciones-y-mejoras-futuras)
* [Contribución](#-contribución)
* [Licencia](#-licencia)

---

## 🚀 Introducción

Este proyecto presenta un **Sistema de Asistencia basado en el Reconocimiento Facial** desarrollado en Python. A diferencia de los métodos tradicionales, que son propensos a errores y consumen mucho tiempo, esta solución aprovecha el poder del reconocimiento facial para automatizar el control de asistencia, ofreciendo una alternativa más eficiente, precisa y rentable. Es ideal para entornos como escuelas, universidades y empresas donde la gestión de asistencia de un gran número de personas es una tarea recurrente. La automatización no solo minimiza el error humano, sino que también previene entradas fraudulentas (como la suplantación de identidad) y libera tiempo valioso para actividades más productivas.

## 🎯 Problema y Motivación

Los sistemas manuales de control de asistencia presentan varios inconvenientes, incluyendo la alta probabilidad de errores, el riesgo de "robo de tiempo" o falsificación de registros, y la considerable carga administrativa asociada a la compilación manual de datos.

Inspirados por la implementación exitosa del reconocimiento facial en grandes empresas tecnológicas como Amazon, Microsoft y Face++ para seguridad, control de acceso e identificación de usuarios, la motivación principal de este proyecto es aplicar conceptos fundamentales de la visión por ordenador y el aprendizaje automático para crear una aplicación práctica y accesible. El objetivo es desarrollar un prototipo de bajo costo que pueda implementarse fácilmente utilizando una cámara web estándar y bibliotecas Python de código abierto, haciéndolo una opción viable para organizaciones con presupuestos limitados.

## ✨ Características

* **Detección y Reconocimiento Facial en Tiempo Real:** Identifica individuos en un flujo de video en vivo.
* **Gestión de Rostros Conocidos:** Carga y codifica una base de datos de imágenes de personas para su reconocimiento.
* **Registro Automatizado de Asistencia:** Marca la asistencia en un archivo CSV con la fecha y hora exactas.
* **Prevención de Duplicados:** Asegura que cada persona sea registrada solo una vez por sesión.
* **Visualización en Vivo:** Muestra el flujo de video con los rostros detectados y sus nombres.
* **Solución de Bajo Costo:** Implementado con herramientas y bibliotecas de código abierto, utilizando hardware de uso común (webcam).

## 🛠️ Tecnologías Utilizadas

* **Lenguaje de Programación:**
    * Python
* **Bibliotecas de Python:**
    * `NumPy`: Para operaciones numéricas eficientes y manejo de datos de imagen como matrices.
    * `OpenCV` (`cv2`): Para procesamiento y manejo de imágenes y captura de video.
    * `face_recognition`: Una biblioteca potente y fácil de usar para detectar, reconocer y manipular caras.
    * `dlib`: Fundamental para la detección y codificación de rostros, proporcionando algoritmos avanzados de machine learning.
    * `cmake`: Una herramienta esencial para configurar y gestionar la compilación de `dlib` y otras bibliotecas.
    * `os`: Para interactuar con el sistema operativo, como listar archivos en directorios.
    * `datetime`: Para manejar fechas y horas en el registro de asistencia.
* **Hardware:**
    * Ordenador portátil o de sobremesa con webcam (para la captura de imágenes).
* **Entorno de Desarrollo:**
    * Cursor (IDE)

## ⚙️ Instalación

### Requisitos Previos

* **Python 3.x**
* Una **webcam** funcional.

### Pasos de Instalación

1.  **Clona este repositorio:**  https://github.com/FrijolitoRaza/TPFinal_FaceRecognition.git
    ```bash
    git clone [https://github.com/FrijolitoRaza/TPFinal_FaceRecognition.git](https://github.com/FrijolitoRaza/TPFinal_FaceRecognition.git)
    cd nombre_del_repositorio
    ```
    
    2.  **Instalar CMake:**
    `dlib` requiere `cmake` para su compilación.
    * **En Windows:** Se recomienda descargar el instalador desde el sitio web oficial de CMake: [https://cmake.org/download/](https://cmake.org/download/). Durante la instalación, asegúrate de marcar la opción "Add CMake to system PATH for all users". Después de la instalación, reinicia tu terminal.
    * **Verificar instalación:** Abre una nueva terminal y ejecuta:
        ```bash
        cmake --version
        ```
        Deberías ver la versión instalada de CMake.
    * **En Linux/macOS:** Generalmente puedes instalar `cmake` a través de tu gestor de paquetes (ej. `sudo apt-get install cmake` o `brew install cmake`).

3.  **Instalar Visual Studio (solo para Windows y si encuentras errores con `dlib`):**
    Si tienes problemas para instalar `dlib` en Windows, es probable que necesites las herramientas de compilación de C++.
    * Descarga **Visual Studio 2022 Community** (versión gratuita) desde: [https://visualstudio.microsoft.com/es/downloads/](https://visualstudio.microsoft.com/es/downloads/).
    * Durante la instalación, asegúrate de seleccionar la carga de trabajo "**Desarrollo para el escritorio con C++**".
    * Una vez instalado, reinicia tu terminal.

4.  **Instala las bibliotecas de Python:**
    Se asume que tienes un archivo `requirements.txt` en la raíz de tu proyecto con las dependencias listadas. Si no, puedes instalar las bibliotecas individualmente:
    ```bash
    pip install -r requirements.txt
    ```
    O individualmente:
    ```bash
    pip install numpy opencv-python face_recognition dlib
    ```

## 🏃 Uso

### Paso 1: Preparar las Imágenes de Rostros Conocidos

1.  Crea un directorio llamado `known_faces` en la raíz de tu proyecto.
2.  Dentro de `known_faces`, coloca imágenes de las personas que deseas que el sistema reconozca.
3.  **Nombra cada archivo de imagen con el nombre completo de la persona** (ej. `Juan_Perez.jpg`, `Maria_Garcia.png`). El sistema utilizará estos nombres para identificar a las personas.
4.  **Actualiza la ruta** en el notebook `*.ipynb` para que apunte a tu directorio `known_faces`.

    ```python
    # En la celda del notebook)
    known_faces_dir = 'known_faces' # O la ruta completa si no está en la raíz del proyecto
    ```
    *(Asegúrate de reemplazar `'C:/Users/Ruta_local'` con la ruta correcta a tu carpeta `known_faces` si no está en la misma raíz que tu script principal).*

### Paso 2: Ejecutar el Sistema

1.  Abre tu terminal o entorno de desarrollo (ej. Cursor, VS Code).
2.  Ejecuta todas las celdas en orden.

El sistema iniciará la cámara web. Cuando detecte un rostro conocido, lo enmarcará con un recuadro verde, mostrará el nombre y registrará la asistencia. Para salir del sistema, presiona la tecla `q` mientras la ventana de la cámara está activa.

## 📊 Registro de Asistencia

La asistencia se registra automáticamente en un archivo llamado `attendance.csv` en el mismo directorio que tu script principal. Este archivo contendrá el nombre de la persona y la fecha y hora exactas de su registro. Cada persona se registrará solo una vez por sesión para evitar duplicados.

Puedes ver el contenido del registro una vez que el programa finalice, como se muestra en la última celda del notebook.

## 💡 Consideraciones y Mejoras Futuras

* **Interfaz de Usuario (GUI):** Implementar una interfaz gráfica más amigable para gestionar los rostros conocidos, visualizar el registro de asistencia y controlar la cámara.
* **Base de Datos:** En lugar de un archivo CSV, usar una base de datos (ej. SQLite, PostgreSQL) para una gestión de asistencia más robusta y escalable.
* **Manejo de Múltiples Caras:** Mejorar la gestión de múltiples caras en una sola imagen (aunque `face_recognition` ya maneja esto, la lógica actual se centra en el `best_match`).
* **Seguridad y Privacidad:** Considerar aspectos de seguridad de los datos biométricos y la privacidad de los usuarios.
* **Robustez:** Mejorar la robustez del sistema frente a variaciones de iluminación, ángulos de la cara, oclusiones, etc.
* **Despliegue:** Contenerizar la aplicación (Docker) para un despliegue más sencillo en diferentes entornos.

## 🤝 Contribución

¡Las contribuciones son bienvenidas! Si deseas mejorar este proyecto, por favor, sigue estos pasos:

1.  Haz un "fork" del repositorio.
2.  Crea una nueva rama (`git checkout -b feature/AmazingFeature`).
3.  Realiza tus cambios y commitea (`git commit -m 'Add some AmazingFeature'`).
4.  Sube tus cambios (`git push origin feature/AmazingFeature`).
5.  Abre un "Pull Request".

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Consulta el archivo `LICENSE` para más detalles.