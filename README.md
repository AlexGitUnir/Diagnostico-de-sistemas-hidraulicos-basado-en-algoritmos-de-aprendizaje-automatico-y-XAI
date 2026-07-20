# Diagnóstico y monitorización de condición de sistemas hidráulicos basado en algoritmos de aprendizaje automático y técnicas XAI
Repositorio que contiene el código Python del Trabajo de Fin de Master titulado Diagnóstico y monitorización de condición de sistemas hidráulicos basado en algoritmos de aprendizaje automático y técnicas XAI.


## Descripción del Proyecto
Este repositorio contiene el código fuente de un Gemelo Digital basado en datos, diseñado para la monitorización predictiva de cuatro subsistemas críticos en una instalación hidráulica: Acumulador, Enfriador, Válvula y Bomba. El proyecto se enmarca en un Trabajo de Fin de Máster y utiliza técnicas de Machine Learning (Random Forest, XGBoost) e Inteligencia Artificial Explicable (XAI) mediante SHAP para proporcionar diagnósticos en tiempo real y explicaciones comprensibles.

La aplicación permite interactuar con un entorno de simulación paramétrica, donde los usuarios pueden modificar variables físicas y observar el impacto en el estado de salud predicho de cada componente, así como las razones detrás de las predicciones de la IA.

## Dataset

Este proyecto utiliza el **Dataset de Sistemas Hidráulicos del Centro de Robótica de la Universidad de California, Irvine (UCI 447)**. Este *dataset* de series temporales multivariadas simula distintos estados de degradación en un banco de pruebas hidráulico, proporcionando lecturas de sensores (presión, temperatura, caudal, vibración, eficiencia) y etiquetas de estado para cuatro componentes: Enfriador, Válvula, Bomba y Acumulador.

## Características Principales

-   **Arquitectura Modular de Subsistemas:** La monitorización se divide en entornos aislados para cada componente. Cada pestaña inicializa su estado nominal óptimo (100% de salud) de forma dinámica, sirviendo como punto de partida para la simulación.
-   **Diagnóstico Dual y Alerta Temprana:** El sistema presenta el 'Estado Predicho' (veredicto discreto del algoritmo) y la 'Confianza Matemática' (probabilidad de pertenencia a la clase), funcionando esta última como una alerta temprana ante la degradación incipiente.
-   **Acoplamiento Físico de Características (Feature Coupling):** Sincroniza dinámicamente las variables estadísticas derivadas (medias, desviaciones estándar, etc.) al alterar un único parámetro físico en la interfaz, garantizando la coherencia termodinámica y matemática del vector de entrada.
-   **Explicabilidad SHAP Dinámica y Resiliente:** Audita las decisiones de la IA mediante gráficos de contribución marginal (Waterfall Plots) basados en la Teoría de Juegos (SHAP). Incorpora tolerancia a fallos para asegurar el renderizado visual incluso ante conflictos de librerías.
-   **Validación de Límites de Inferencia:** Los controles interactivos están restringidos a los rangos operacionales del *dataset* histórico de entrenamiento, previniendo errores por extrapolación a zonas desconocidas.


## Configuración y Ejecución del Gemelo Digital

Sigue estos pasos para poner en marcha la aplicación Streamlit en tu máquina local:

### 1. Requisitos Previos

Necesitarás Python instalado en tu sistema. Puedes descargarlo desde el sitio oficial: [python.org](https://www.python.org/downloads/)

### 2. Descarga de Archivos

Descarga los siguientes archivos y carpetas en tu máquina:
-   `gemelo_digital.py` (el script principal de Streamlit).
-   La carpeta `deploy/` (contiene los modelos entrenados y *encoders*).

Coloca tanto el archivo `gemelo_digital.py` como la carpeta `deploy/` en el mismo directorio (por ejemplo, `C:\Users\TuUsuario\ProyectoGemeloDigital`).

### 3. Instalación de Librerías

Abre una terminal o símbolo del sistema (CMD) y ejecuta el siguiente comando para instalar todas las dependencias necesarias:

```bash
pip install streamlit pandas joblib shap matplotlib numpy xgboost scikit-learn
```

### 4. Ejecución del Gemelo Digital

Una vez instaladas las librerías, ejecuta la aplicación Streamlit desde tu terminal:

```bash
streamlit run gemelo_digital.py
```

Esto abrirá automáticamente la interfaz del Gemelo Digital en tu navegador web, generalmente en `http://localhost:8501`.

## Estructura del Repositorio

```

├── gemelo_digital.py           # Script principal de la aplicación Streamlit
└── deploy/                     # Carpeta que contiene los artefactos del modelo
    ├── modelo_acumulador.pkl   # Modelo entrenado para el acumulador
    ├── le_acumulador.pkl       # Label Encoder para el acumulador
    ├── modelo_enfriador.pkl    # Modelo entrenado para el enfriador
    ├── le_enfriador.pkl        # Label Encoder para el enfriador
    ├── modelo_valvula.pkl      # Modelo entrenado para la válvula
    ├── le_valvula.pkl          # Label Encoder para la válvula
    ├── modelo_bomba.pkl        # Modelo entrenado para la bomba
    ├── le_bomba.pkl            # Label Encoder para la bomba
    └── datos_simulacion.csv    # Datos de referencia para la simulación
```


## Contacto

alejandro.valdeolmillos808@comunidadunir.net
