# 📊 ConnectaTel: Análisis Exploratorio de Datos (EDA) y Segmentación de Clientes

Este proyecto realiza un **Análisis Exploratorio de Datos (EDA)** detallado sobre la base de usuarios de **ConnectaTel**, una empresa de telecomunicaciones ficticia. El objetivo principal es diagnosticar los hábitos de consumo de los clientes (edad, mensajes, llamadas y minutos) y proponer estrategias de negocio basadas en datos, como la detección de usuarios ideales para campañas de actualización de plan (*Upselling*) y la mitigación de riesgos de fuga (*Churn*).

---

## 🎯 Objetivo del Proyecto

El análisis busca resolver preguntas clave de negocio para optimizar la toma de decisiones y la rentabilidad de ConnectaTel:
1. **Identificar anomalías y outliers:** Detectar errores de registro (como valores de control en la edad) y aislar comportamientos de consumo atípico utilizando técnicas estadísticas como el **Rango Intercuartílico (IQR)**.
2. **Entender los hábitos de consumo:** Evaluar cómo varía la cantidad de mensajes, llamadas y minutos consumidos entre los clientes del **Plan Básico** y el **Plan Premium**.
3. **Crear segmentos de negocio:** Clasificar a la población de usuarios a través de variables demográficas y de comportamiento digital para diseñar campañas de marketing hiper-dirigidas.

---

## 💾 Datasets Utilizados

El proyecto opera bajo un ecosistema de datos consolidado que vincula la información del cliente con su historial de uso mensual. Las variables principales procesadas son:

* `user_id`: Identificador único de cada usuario.
* `age`: Edad del cliente (se procesó una limpieza para corregir valores atípicos artificiales de control como `-999`).
* `plan`: Tipo de plan contratado (`Basico` o `Premium`).
* `mensajes_enviados`: Cantidad total de SMS transmitidos en el periodo.
* `llamadas_realizadas`: Frecuencia total de llamadas telefónicas iniciadas por el usuario.
* `minutos_consumidos`: Duración acumulada de las llamadas (variable crítica sujeta a penalizaciones por exceso en el Plan Básico al superar los 100 minutos).

---

## ⚙️ Etapas del Análisis Realizadas

El flujo de trabajo en el Jupyter Notebook se estructuró en cinco fases metodológicas:

1.  **Limpieza y Preparación de Datos:** Identificación y corrección de valores atípicos demográficos (`age = -999`) sustituyéndolos por la mediana de la población para salvaguardar la consistencia estadística.
2.  **Análisis de Distribuciones (Histogramas & KDE):** Implementación de gráficos distribucionales segmentados por `plan` utilizando `Seaborn`. Se descubrió que la mensajería tradicional está en desuso y que el verdadero reto de negocio radica en los minutos de voz consumidos.
3.  **Detección e Ingeniería de Outliers (Método IQR):** Construcción automatizada de diagramas de caja (*Boxplots*) en cuadrículas de 2x2 con títulos dinámicos. Aplicación de un bucle matemático iterativo para determinar los límites superiores exactos mediante la regla de Tukey:
    $$\text{Límite Superior} = Q_3 + (1.5 \times \text{IQR})$$
    *Decisión estratégica:* Mantener los outliers de minutos por representar un alto valor comercial de conversión y riesgo.
4.  **Ingeniería de Características (*Feature Engineering*):** Creación vectorizada de la variable métrica `grupo_uso` mediante `np.select()` bajo condiciones jerárquicas lógicas (*Bajo uso*, *Uso medio* y *Alto uso*), además de la agrupación por rangos biológicos en `grupo_edad`.
5.  **Análisis Categórico Agrupado:** Visualizaciones ejecutivas (`sns.countplot`) cruzando los nuevos segmentos con la variable `plan` para formular planes de acción inmediatos.

---

## 🚀 Cómo Ejecutar el Notebook

El entorno está preparado para ser reproducido localmente o en la nube de forma ágil.

### Opción A: Ejecución en Google Colab (Recomendado)
1. Descarga el archivo `.ipynb` desde este repositorio.
2. Ve a [Google Colab](https://colab.research.google.com/) e inicia sesión con tu cuenta de Google.
3. Haz clic en **Archivo** > **Subir bloc de notas** y selecciona el archivo descargado.
4. Si requieres cargar los archivos de datos de forma directa, puedes subirlos a la sección de archivos del panel izquierdo en Colab.

### Opción B: Ejecución Local (Jupyter Lab / Notebook)
Asegúrate de contar con una distribución de Python 3.8+ instalada (como Anaconda) y ejecuta en tu terminal:
```bash
pip install pandas numpy matplotlib seaborn
jupyter lab
