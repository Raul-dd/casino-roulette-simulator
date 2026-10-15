#  Casino Roulette Simulator

<p align="center">
  <strong>Simulador de ruleta europea desarrollado en Bash</strong>
  <br>
  Una herramienta de terminal para explorar estrategias de apuestas, probabilidades y administración de capital mediante simulaciones.
</p>

<p align="center">
  <a href="https://github.com/Raul-dd/casino-roulette-simulator">
    <img src="https://img.shields.io/badge/Project-Bash%20Simulator-222222?style=for-the-badge&logo=gnubash&logoColor=white" alt="Bash Simulator">
  </a>
  <img src="https://img.shields.io/badge/Platform-Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black" alt="Linux">
  <img src="https://img.shields.io/badge/Interface-CLI-2EA44F?style=for-the-badge&logo=windowsterminal&logoColor=white" alt="Command Line Interface">
  <img src="https://img.shields.io/badge/Language-Bash-4EAA25?style=for-the-badge&logo=gnubash&logoColor=white" alt="Bash">
</p>

<p align="center">
  <a href="#-descripción">Descripción</a> •
  <a href="#-características">Características</a> •
  <a href="#-instalación-y-uso">Instalación</a> •
  <a href="#-estrategias-implementadas">Estrategias</a> •
  <a href="#-consideraciones">Consideraciones</a>
</p>

---

## Descripción

**Casino Roulette Simulator** es un proyecto de línea de comandos desarrollado con Bash que reproduce rondas de una ruleta europea para experimentar con diferentes estrategias de apuestas.

El programa genera resultados entre `0` y `36`, permite establecer un capital inicial y ofrece dos métodos de gestión de apuestas: Martingala y Labouchère inversa.

Su ejecución se realiza desde la terminal mediante argumentos, mientras que la interacción durante la simulación permite seleccionar apuestas a números pares o impares.

El proyecto está orientado al aprendizaje de scripting en Bash, estructuras de control, operaciones aritméticas, generación de valores aleatorios y automatización de procesos en la terminal.

##  Características

- **Simulación de ruleta europea:** generación de resultados del 0 al 36.
-  **Capital inicial configurable:** define el dinero virtual con el que comienza la simulación.
-  **Estrategia Martingala:** duplica la apuesta tras una pérdida y vuelve a la apuesta inicial después de una victoria, según la lógica implementada.
-  **Labouchère inversa:** utiliza una secuencia numérica para calcular y ajustar las apuestas.
-  **Selección de apuestas:** permite apostar continuamente a números pares o impares.
-  **Interfaz de terminal a color:** mensajes visuales para distinguir eventos y resultados.
-  **Información de la sesión:** muestra datos sobre las jugadas y el capital durante la ejecución, según la estrategia seleccionada.
-  **Ejecución mediante argumentos:** configura el capital y la estrategia sin modificar el código fuente.

##  Tecnologías utilizadas

| Tecnología | Aplicación |
|---|---|
| **Bash** | Lógica principal y automatización del simulador. |
| **Shell scripting** | Parámetros, funciones, ciclos y estructuras condicionales. |
| **`$RANDOM`** | Generación de resultados pseudoaleatorios. |
| **`getopts`** | Procesamiento de argumentos de línea de comandos. |
| **ANSI escape sequences** | Colores y formato de la salida en terminal. |
| **`tput`** | Control de la visibilidad del cursor en terminales compatibles. |

##  Requisitos

Antes de ejecutar el simulador, asegúrate de contar con:

- Un entorno Linux o compatible con Bash.
- Bash instalado.
- Git para clonar el repositorio.
- Una terminal compatible con los controles de cursor utilizados por el script.

No requiere frameworks web, bases de datos ni dependencias de Composer o NPM.

##  Instalación y uso

### 1. Clonar el repositorio

```bash
git clone https://github.com/Raul-dd/casino-roulette-simulator.git
```

### 2. Acceder al directorio

```bash
cd casino-roulette-simulator
```

### 3. Dar permisos de ejecución

```bash
chmod +x ruleta.sh
```

### 4. Ejecutar el simulador

La sintaxis general es:

```bash
./ruleta.sh -m <capital_inicial> -t <estrategia>
```

Parámetros disponibles:

| Parámetro | Descripción |
|---|---|
| `-m` | Capital inicial para la simulación. |
| `-t` | Estrategia de apuestas que se utilizará. |
| `-h` | Opción reservada en el script; para consultar el uso, ejecuta el programa sin argumentos. |

###  Ejemplos de ejecución

**Opción 1 — Estrategia Martingala**

```bash
./ruleta.sh -m 1000 -t martingala
```

Inicia la simulación con un capital de `1000` unidades virtuales. El programa solicita la apuesta inicial y la elección entre pares e impares.

**Opción 2 — Estrategia Labouchère inversa**

```bash
./ruleta.sh -m 1000 -t inverseLabrouchere
```

Inicia la simulación con el mismo capital y aplica la estrategia basada en una secuencia numérica.

> **Importante:** Los nombres de las estrategias deben escribirse exactamente como aparecen en los ejemplos, respetando las mayúsculas y minúsculas.

##  Estrategias implementadas

### 1.  Martingala

La Martingala es un método de progresión de apuestas que incrementa la cantidad apostada después de una pérdida y restablece la apuesta inicial después de una victoria.

**Funcionamiento general:**

1. Se define el capital inicial.
2. Se establece una apuesta inicial.
3. Se elige apostar a pares o impares.
4. Después de una pérdida, la siguiente apuesta se duplica.
5. Después de una victoria, la apuesta vuelve a su valor inicial.
6. La simulación continúa hasta que se alcanza la condición de finalización del programa.

**Objetivo de aprendizaje:** observar cómo una progresión de apuestas afecta al capital disponible y cómo las pérdidas consecutivas pueden incrementar rápidamente el riesgo.

### 2.  Labouchère inversa

Esta estrategia utiliza una secuencia numérica para determinar la cantidad de las apuestas.

En la implementación actual, la secuencia inicial es:

```text
[1, 2, 3, 4]
```

La apuesta inicial se calcula sumando los extremos de la secuencia:

```text
1 + 4 = 5
```

**Funcionamiento general:**

1. Se inicializa la secuencia numérica.
2. Se calcula la apuesta a partir de los extremos.
3. Se genera un resultado de la ruleta.
4. La secuencia se modifica según el resultado de la apuesta.
5. Se reajustan la secuencia y determinados umbrales de capital de acuerdo con la lógica del script.

**Objetivo de aprendizaje:** analizar la relación entre las secuencias de apuestas, las pérdidas, las ganancias y la evolución del capital.

> Las descripciones anteriores resumen el comportamiento previsto de las estrategias. La lógica exacta del código determina los resultados de cada sesión.

##  ¿Cómo funciona la simulación?

El flujo general del programa es el siguiente:

```text
Inicio
  │
  ▼
Definir capital inicial
  │
  ▼
Seleccionar estrategia
  │
  ├── Martingala
  │
  └── Labouchère inversa
          │
          ▼
  Elegir pares o impares
          │
          ▼
  Generar resultado (0–36)
          │
          ▼
  Evaluar apuesta y actualizar capital
          │
          ▼
  Ajustar apuesta o secuencia
          │
          ▼
  Continuar hasta la condición de salida
```

##  Estructura del repositorio

```text
casino-roulette-simulator/
└── ruleta.sh    # Script principal del simulador
```

El proyecto concentra la lógica de ejecución en un único archivo Bash, lo que facilita su lectura, ejecución y modificación.

##  Consideraciones importantes

- **Simulación educativa:** el programa utiliza dinero virtual y no se conecta a casinos ni realiza apuestas reales.
- **Sin garantías de ganancias:** ninguna de las estrategias elimina la ventaja matemática de la casa ni garantiza resultados positivos.
- **Riesgo de progresión:** duplicar apuestas puede provocar que el capital se agote rápidamente durante una racha de pérdidas.
- **Resultados pseudoaleatorios:** los valores generados por `$RANDOM` no constituyen una fuente criptográficamente segura.
- **Validación de entradas:** utiliza valores numéricos positivos para el capital y la apuesta inicial. La implementación actual no valida de forma exhaustiva todas las entradas posibles.

##  Mejoras futuras

- [ ] Validación robusta de argumentos y valores introducidos.
- [ ] Incorporación de un menú interactivo para seleccionar estrategias.
- [ ] Resumen final con balance, ganancias, pérdidas y número de rondas.
- [ ] Registro de resultados en un archivo.
- [ ] Configuración de límites de apuesta y capital.
- [ ] Pruebas automatizadas y análisis estático del script.
- [ ] Separación de la lógica de simulación y la presentación en terminal.

Estas propuestas representan posibles ampliaciones, no funcionalidades que necesariamente estén disponibles en la versión actual.

##  Contribuciones

Las sugerencias y mejoras son bienvenidas.

1. Realiza un *fork* del repositorio.
2. Crea una rama para tu modificación.
3. Implementa y prueba los cambios.
4. Abre un *pull request* con una descripción clara de tu propuesta.

------

<p align="center">
  <strong> Casino Roulette Simulator</strong>
  <br>
  <sub>Bash scripting · Simulación probabilística · Estrategias de apuestas</sub>
  <br><br>
  Desarrollado por <a href="https://github.com/Raul-dd">Raul-dd</a>
  <br>
  <a href="https://github.com/Raul-dd/casino-roulette-simulator">Ver repositorio en GitHub</a>
</p>
