# Modelo de Optimización en Etapas

Este repositorio contiene el código fuente y los datos de ejemplo para el proyecto de tesis de Maestría en Matemática Computacional titulado: "IMPLEMENTACIÓN DE UN MODELO MATEMÁTICO DE OPTIMIZACIÓN PARA LA ASIGNACIÓN DE HORARIOS DE CLASE Y RECURSOS TECNOLÓGICOS MEDIANTE PYTHON EN UN INSTITUTO DE LENGUAS EXTRANJERAS, #PERIODO 2024-6B".

## Descripción del Proyecto

El proyecto consiste en un marco de optimización matemática secuencial en tres etapas, diseñado para resolver el problema de asignación de recursos en el Instituto de Lenguas Extranjeras para un ciclo académico específico. El objetivo es automatizar y optimizar la asignación de:

1.  **Profesores a Clases:** Maximizando preferencias y cumpliendo restricciones de carga y aptitud.
2.  **Cuentas de Videoconferencia:** Minimizando el uso de licencias y respetando complejas reglas de compartición.
3.  **Libros Digitales:** Minimizando el uso de licencias distintas y garantizando compatibilidad.

El sistema está implementado en Python utilizando la librería `PuLP` para el modelado y el solver `CBC` para la resolución.

## Estructura del Repositorio

```
.
├── asignacion_etapa1.py      # Script principal para ejecutar la Etapa 1
├── asignacion_etapa2.py      # Script principal para ejecutar la Etapa 2
├── asignacion_etapa3.py      # Script principal para ejecutar la Etapa 3
├── datos/
│   ├── datos_clases.xlsx     # Archivo de entrada con la lista de clases
│   ├── datos_profesores.xlsx # Archivo de entrada con profesores y preferencias
├── resultados/
│   ├── asignacion_profesores_E1.xlsx # Archivo de salida de la Etapa 1
│   ├── asignacion_VC_E2.xlsx         # Archivo de salida de la Etapa 2
│   └── asignacion_libros_E3.xlsx     # Archivo de salida de la Etapa 3
└── LEEME.md                 # Este archivo
```

## Requisitos de Instalación

Para ejecutar los scripts, se requiere Python 3.x y las siguientes librerías. Se recomienda utilizar un entorno virtual.

1.  **Instalar Python:** Asegúrate de tener una versión de Python 3.8 o superior.
2.  **Instalar Librerías:** Ejecuta el siguiente comando en tu terminal:
    ```bash
    pip install pulp pandas openpyxl
    ```
3.  **Solver CBC:** PuLP intentará usar el solver CBC que viene empaquetado. Si por alguna razón no funciona, puede ser necesario instalarlo por separado o asegurarse de que esté en el PATH del sistema.

## Estructura de los Datos de Entrada

Para ejecutar el modelo para un nuevo ciclo, se deben actualizar los archivos Excel ubicados en la carpeta `datos/`.

*   **`datos_clases.xlsx`**: Debe contener las columnas `Modulo`, `Horario`, `Paralelo`.
*   **`datos_profesores.xlsx`**: Debe contener una columna `Profesor`, una columna `Clases` (carga máxima/objetivo), y columnas binarias (0/1) para cada módulo (e.g., `B1`, `B2`...) y cada horario (e.g., `08H00-10H00`...).

## Ejecución del Modelo

El proceso debe ejecutarse de forma secuencial. Ejecuta los scripts desde la terminal en el directorio raíz del proyecto:

1.  **Ejecutar Etapa 1:**
    ```bash
    python asignacion_etapa1.py
    ```
    Esto generará el archivo `resultados/asignacion_profesores_E1.xlsx`.

2.  **Ejecutar Etapa 2:**
    ```bash
    python asignacion_etapa2.py
    ```
    Esto leerá la salida de la Etapa 1 y generará `resultados/asignacion_VC_E2.xlsx`.

3.  **Ejecutar Etapa 3:**
    ```bash
    python asignacion_etapa3.py
    ```
    Esto leerá la salida de la Etapa 1 y generará `resultados/asignacion_libros_E3.xlsx`, completando el proceso.

## Autor

*   **[Juan José Viscaíno Gavilánes]**

## Licencia

Este proyecto se presenta como parte de la tesis de Maestría en Matemática Computacional. El código es para fines académicos y de demostración.
