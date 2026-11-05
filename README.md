# 📈 Modelado Predictivo de Volatilidad y Retornos en Activos Digitales (BTC-USD)

**Autor:** César Ciro Garro Sánchez | *Economista Senior y Científico de Datos Financieros*  
**Tecnologías:** Python, Pandas, NumPy, Scikit-Learn, yfinance.

---

## 📌 Resumen Ejecutivo
Este repositorio contiene un análisis econométrico y de Ciencia de Datos aplicado a la serie de tiempo diaria de Bitcoin (2020-2026). El objetivo principal del modelo es auditar empíricamente la predictibilidad del mercado cripto, contrastando la proyección de **retornos direccionales** frente a la predicción de **turbulencia (Volatility Clustering)** mediante modelos de Regresión Lineal sobre rezagos temporales (*lags*).

## 🧠 El Problema: Precio vs. Riesgo
En la gestión de portafolios de alta capitalización, la predicción del precio exacto a corto plazo es matemáticamente ineficiente debido a la naturaleza de paseo aleatorio (*Random Walk*) de los mercados. Sin embargo, **el riesgo sí tiene memoria**. Este proyecto demuestra cómo aislar estadísticamente el agrupamiento de volatilidad para anticipar regímenes de alta turbulencia.

## ⚙️ Metodología Técnica
1. **Extracción y Limpieza:** Consumo de datos reales vía API y cálculo de retornos logarítmicos continuos para mitigar la asimetría estadística.
2. **Feature Engineering (Ingeniería de Datos):** Construcción de variables predictoras mediante técnicas de desplazamiento (*shifting*) en Pandas para crear ventanas de 5 rezagos.
3. **Validación Estricta:** División cronológica secuencial (80% Train / 20% Test) para eliminar por completo el sesgo de anticipación (*look-ahead bias*).
4. **Benchmarking:** Evaluación de los modelos de Machine Learning (Regresión Lineal) frente a modelos predictivos ingenuos (*Naive Base*).

## 📊 Resultados del Modelado

* **Retornos Direccionales (Eficiencia de Mercado):** El modelo confirma que intentar predecir el retorno diario con rezagos simples no supera al azar. El RMSE del modelo predictivo (0.02185) es estadísticamente idéntico al modelo ingenuo, con una tasa de acierto direccional del 50%.
* **Predictibilidad de la Volatilidad (Volatility Clustering):** Al modelar el retorno absoluto (proxy del riesgo), el modelo predictivo supera con éxito la base ingenua, reduciendo el RMSE a 0.0160. Se comprueba matemáticamente que **los picos de turbulencia en criptoactivos están autocorrelacionados y son predecibles**.

## 💼 Impacto Financiero y Gestión de Portafolio
Este hallazgo cuantitativo se traduce en algoritmos directos para la protección de capital institucional:
* **Dynamic Position Sizing:** Reducción automática de la exposición de capital al detectar algorítmicamente el inicio de un clúster de alta varianza.
* **Stop-Loss Inteligentes:** Ampliación o contracción dinámica de los límites de pérdida para evitar cierres prematuros (*whipsaws*) provocados por el ruido natural del mercado.
* **DCA Optimizado (Dollar Cost Averaging):** Ejecución algorítmica de compras escalonadas maximizadas durante regímenes proyectados de baja volatilidad.

---
*Para auditar el código fuente, la limpieza de datos y las métricas de error, revise el cuaderno `Forecasting_con_ML.ipynb` incluido en este repositorio.*
