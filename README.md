# Análisis Cuantitativo de Activos Tecnológicos

Este repositorio contiene un entorno de análisis cuantitativo exhaustivo aplicado a un portafolio de 8 activos tecnológicos líderes en el mercado global. Utilizando técnicas avanzadas de modelado matemático, estadístico y ciencia de datos, el proyecto desglosa el comportamiento de los rendimientos financieros, evalúa el riesgo regulatorio y simula trayectorias de rendimiento a futuro.

## 📋 Contenido del Notebook

El análisis está estructurado en las siguientes fases lógicas:
1. **Contexto y Objetivos:** Planteamiento de las preguntas fundamentales de negocio e inversión.
2. **Metodología y Preparación:** Adquisición de datos históricos y transformación a rendimientos logarítmicos.
3. **Análisis Exploratorio de Datos (EDA):** Estadísticas descriptivas, rendimientos acumulados y matrices de correlación sectorial.
4. **Modelado Estadístico (Hallazgos Clave):** Pruebas formales de normalidad (Shapiro-Wilk) y bondad de ajuste a distribuciones de colas pesadas (t de Student).
5. **Análisis de Riesgo y Proyecciones:** Medición del Value at Risk (VaR) histórico al 99% y simulación estocástica de Monte Carlo para proyecciones futuras.
6. **Inferencia Bayesiana:** Actualización de probabilidades de crecimiento combinando simulaciones, rendimientos históricos y datos reales del mercado.
7. **Clustering de Activos:** Agrupación jerárquica de activos basada en distancias de correlación para estrategias de diversificación inteligente.
8. **Análisis de Dependencia Temporal:** Evaluación de autocorrelación a través de gráficos ACF y PACF.

---

## 💻 Arquitectura de Datos y Flujo del Proceso

El ciclo de vida del dato dentro del notebook sigue el siguiente flujo de transformaciones y modelos estadísticos:

```mermaid
graph TD
    A[Inicio: Selección de Tickers] --> B{yfinance API};
    B --> C[DataFrame: Precios de Cierre Diarios];
    C --> D{Cálculo de Rendimientos Logarítmicos};
    D --> E[DataFrame: log_returns];
    
    E --> F[EDA & Matriz de Correlación];
    E --> G{Prueba Shapiro-Wilk};
    G -- p-valor < 0.05 --> H[Rechazo de Normalidad / Colas Pesadas];
    
    E --> I{Ajuste t de Student & Prueba K-S};
    I -- p-valor > 0.05 --> J[Validación de Distribución t-Student];
    
    E --> K[Análisis de Riesgo: VaR Histórico 99%];
    E --> L{Simulación de Monte Carlo 10k sims};
    
    L --> M[Probabilidad Prior de Crecimiento];
    M --> N{Teorema de Bayes};
    N --> O[Probabilidad Posterior Actualizada];
    
    E --> P[Clustering Jerárquico Ward];
    E --> Q[Análisis Temporal ACF/PACF];
    
    H & J & K & O & P & Q --> R[Fin: Decisiones Estratégicas de Inversión];
