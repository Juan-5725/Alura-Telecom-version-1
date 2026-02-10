# Análisis de Evasión de Clientes en TelecomX

## Tabla de Contenidos

- [Introducción](#introducción)
- [Fuente de Datos](#fuente-de-datos)
- [Objetivo del Proyecto](#objetivo-del-proyecto)
- [Análisis Exploratorio de Datos (EDA)](#análisis-exploratorio-de-datos-eda)
  - [Distribución de Evasión](#distribución-de-evasión)
  - [Factores Demográficos](#factores-demográficos)
  - [Contrato y Servicios de Internet](#contrato-y-servicios-de-internet)
  - [Métodos de Pago](#métodos-de-pago)
  - [Tiempo de Contratación y Cargos](#tiempo-de-contratación-y-cargos)
- [Conclusiones Clave](#conclusiones-clave)
- [Recomendaciones Estratégicas](#recomendaciones-estratégicas)
- [Tecnologías Utilizadas](#tecnologías-utilizadas)

## Introducción

Este proyecto se centra en el análisis de la evasión (churn) de clientes de una empresa de telecomunicaciones ficticia, TelecomX. El objetivo principal es identificar los factores que contribuyen a que los clientes abandonen el servicio, comprender patrones de comportamiento y proponer recomendaciones estratégicas para mejorar la retención de clientes.

La evasión de clientes es un problema crítico para las empresas de telecomunicaciones, ya que la adquisición de nuevos clientes suele ser más costosa que la retención de los existentes. Mediante un análisis detallado de los datos, buscamos obtener insights accionables para mitigar este fenómeno.

## Fuente de Datos

El dataset utilizado para este análisis se obtuvo de un recurso público (`https://raw.githubusercontent.com/ingridcristh/challenge2-data-science/refs/heads/main/TelecomX_Data.json`). Contiene información detallada sobre los clientes de TelecomX, incluyendo:

- **Información del Cliente:** Género, si es un cliente senior, si tiene pareja o dependientes, y el tiempo de permanencia (tenure).
- **Servicios Contratados:** Servicios telefónicos (líneas múltiples), servicios de internet (tipo, seguridad online, backup, protección de dispositivo, soporte técnico, streaming de TV/películas).
- **Información de la Cuenta:** Tipo de contrato, facturación sin papel, método de pago, cargos mensuales y cargos totales.
- **Variable Objetivo:** `Churn` (si el cliente canceló el servicio).

## Objetivo del Proyecto

1.  **Limpieza y Preprocesamiento de Datos:** Manejar valores nulos, duplicados y transformar tipos de datos para asegurar la calidad de los datos.
2.  **Análisis Exploratorio de Datos (EDA):** Visualizar la distribución de la evasión y explorar la relación entre `Churn` y las demás variables del dataset (demográficas, de servicio, de cuenta).
3.  **Identificación de Factores Clave:** Determinar qué variables tienen mayor impacto en la decisión de un cliente de evadir el servicio.
4.  **Generación de Conclusiones y Recomendaciones:** Basado en el análisis, formular conclusiones claras y proponer estrategias concretas para reducir la tasa de evasión.

## Análisis Exploratorio de Datos (EDA)

Se realizaron varias visualizaciones para entender mejor el comportamiento de los clientes y los patrones de evasión:

### Distribución de Evasión

- Se calculó la tasa general de evasión, revelando que aproximadamente el **26.5%** de los clientes han abandonado el servicio. Esto fue visualizado con un gráfico de pastel.

### Factores Demográficos

- Se analizó la evasión por género y por la condición de 'SeniorCitizen'. No se encontraron diferencias significativas en la tasa de evasión por género, ni una correlación fuerte con ser Senior Citizen.

### Contrato y Servicios de Internet

- El **tipo de contrato** demostró ser un factor crucial: los clientes con contratos **mes a mes** presentan una tasa de evasión considerablemente más alta en comparación con los contratos de uno o dos años. Esto se visualizó con gráficos de barras.
- Los servicios de **Internet de Fibra Óptica**, especialmente combinados con contratos mes a mes, muestran una alta propensión a la evasión, destacado en un gráfico sunburst.

### Métodos de Pago

- El **cheque electrónico** fue identificado como el método de pago con la tasa de evasión más alta. Esto sugiere posibles problemas de satisfacción o experiencia con este método o con el segmento de clientes que lo utiliza.

### Tiempo de Contratación y Cargos

- Los clientes que evaden tienden a tener un **tiempo de permanencia significativamente más corto** y **cargos totales más bajos** en comparación con los clientes que permanecen. Sin embargo, tienden a tener **cargos mensuales más altos**.
- Los gráficos de dispersión y box plots mostraron claramente la relación entre `customer.tenure`, `account.Charges.Monthly`, `account.Charges.Total` y `Churn`.
- Se calculó una matriz de correlación entre las variables numéricas, confirmando una alta correlación entre `customer.tenure` y `account.Charges.Total`.

## Conclusiones Clave

1.  **Alta Tasa de Evasión:** La empresa enfrenta un desafío significativo con un ~26.5% de sus clientes abandonando el servicio.
2.  **Riesgo de Contratos Mes a Mes:** Este tipo de contrato es un fuerte predictor de evasión, lo que implica una menor lealtad del cliente.
3.  **Evasión Temprana:** Los clientes con menor tiempo de permanencia son los más propensos a cancelar, especialmente en los primeros meses de servicio.
4.  **Método de Pago Problemático:** El cheque electrónico está asociado con un mayor riesgo de abandono.
5.  **Servicio de Fibra Óptica:** A pesar de ser un servicio premium, los clientes de fibra óptica con contratos cortos tienen una alta tasa de evasión.
6.  **Disparidad en Cargos:** Los clientes que evaden pagan más mensualmente, pero menos en total debido a su corta permanencia.

## Recomendaciones Estratégicas

1.  **Incentivar Contratos a Largo Plazo:** Ofrecer descuentos, beneficios adicionales (ej. mejoras de servicio, equipos gratis) o tarifas más competitivas para promover contratos de uno o dos años.
2.  **Monitoreo Proactivo y Programas de Bienvenida:** Implementar un sistema para identificar y contactar proactivamente a clientes en riesgo (especialmente nuevos clientes con <6-12 meses de antigüedad y contratos mes a mes), con programas de bienvenida mejorados y encuestas de satisfacción tempranas.
3.  **Optimizar la Experiencia con Cheques Electrónicos:** Investigar a fondo la razón detrás de la alta tasa de evasión asociada a los cheques electrónicos (usabilidad, confiabilidad, tipo de cliente) y, si es posible, ofrecer incentivos para migrar a métodos de pago automáticos (tarjeta de crédito, transferencia bancaria).
4.  **Claridad y Valor en Ofertas de Fibra Óptica:** Asegurar que los clientes de fibra óptica comprendan completamente el valor y los términos de su servicio, especialmente si tienen cargos mensuales altos y contratos flexibles. Mejorar el soporte técnico para este segmento.
5.  **Análisis de Cargos Mensuales Altos:** Segmentar a los clientes con cargos mensuales elevados para entender su satisfacción y la percepción de valor. Ofrecer planes personalizados para evitar la percepción de costos excesivos o servicios no utilizados.

## Tecnologías Utilizadas

- **Python** (versión 3.x)
- **Pandas:** Para manipulación y análisis de datos.
- **NumPy:** Para operaciones numéricas.
- **Plotly Express:** Para visualizaciones interactivas.
- **Seaborn:** Para visualizaciones estadísticas.
- **Matplotlib:** Para visualizaciones básicas.
- **Requests:** Para la descarga del dataset desde la URL.
