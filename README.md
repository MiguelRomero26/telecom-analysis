# telecom-analysis
## 📡 Análisis de Clientes · ConnectaTel

Proyecto de análisis de datos sobre el comportamiento de clientes de una
empresa de telecomunicaciones en Latinoamérica durante el año 2024.

### 🎯 Objetivos
- Limpiar y validar tres datasets: planes, usuarios y uso de servicios
- Construir un perfil estadístico de los clientes
- Detectar valores inválidos, sentinels y outliers
- Segmentar clientes por nivel de uso y grupo de edad
- Generar recomendaciones de retención y mejora de planes

### 🗂️ Datasets
| Archivo | Descripción |
|---|---|
| `plans.csv` | Planes disponibles, precios y costos por excedente |
| `users_latam.csv` | Clientes: edad, ciudad, plan contratado y churn |
| `usage.csv` | Eventos de uso: llamadas y mensajes por cliente |

### 🛠️ Tecnologías
`Python` · `pandas` · `numpy` · `seaborn` · `matplotlib` · `scikit-learn`

### 📊 Principales hallazgos
- Base de clientes madura: 78 % adultos y seniors
- 73.5 % de los clientes tienen uso medio dentro de su plan
- 19.5 % en bajo uso → riesgo de churn silencioso
- Segmento joven (21 %) subrepresentado y con patrones distintos
