<p align="center"><b><font size="5">Predicción de impago en tarjetas de crédito con modelos clásicos de machine learning y redes neuronales</font></b></p>

**Resultados principales:**

-	Recall de 0.74 en producción
-	XGBoost como mejor modelo
-	Inferencia de 0.000008 s por observación
-	Aplicación desplegada en Streamlit

**Descripción y meta del proyecto:**

El objetivo del proyecto es desarrollar una aplicación capaz de predecir el impago de tarjetas de crédito utilizando modelos de machine learning y redes neuronales. Se evalúan varios modelos buscando los mejores tiempos de entrenamiento y se usa el recall como métrica principal, suponiendo que es más costoso no detectar un cliente que caerá en impago que incluir un cliente en impago de forma errónea.
El resultado de este desarrollo es una aplicación al que se le puede proporcionar un dataset o generar observaciones aleatorias. El resultado es la predicción de impago, la proporción pago-impago y la tabla generada aleatoriamente o proporcionada manualmente junto con la probabilidad de pago-impago en cada observación. 

<img width="298" height="197" alt="image" src="https://github.com/user-attachments/assets/a81fb25d-2438-424b-bcf8-faca097ab96b" />
<img width="284" height="199" alt="image" src="https://github.com/user-attachments/assets/4ef9b448-a8ff-4514-b60f-6146e0022a99" />

**Dataset:**

El dataset usado es de libre acceso de Machine learning repository: El dataset es sobre los impagos de tarjetas de crédito de Taiwan. Contiene 24 columnas y 30000 observaciones. https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients

**Métricas:**

La métrica principal es el recall considerando que no detectar un cliente que no pagará es más costoso que clasificar a un cliente erróneamente con una alta probabilidad de impago. También se consideran los mejores tiempos de entrenamiento y de predicción.

**Modelos utilizados:**

-	Logistic Regression
-	Random Forest, XGBoost
-	SVC 
-	Feedforward Neural Network (FNN)

**Archivos principales:**

-	credito.py: aplicación Streamlit desplegada
-	Predicción de impago en tarjetas de credito.ipynb: análisis completo y desarrollo del modelo.

**Tecnologías utilizadas:**

-	Python
-	Pandas
-	NumPy
-	PyTorch
-	Streamlit
-	GitHub
-	Matplotlib
-	Seaborn

**Técnicas de preprocesamiento:**

- Winsorization
-	SMOTE

**Resultados:**

<img width="379" height="139" alt="image" src="https://github.com/user-attachments/assets/dea19661-0427-4b7b-bb0a-d132fd339c76" />

**Al modificar el umbral y el learning rate a 0.05 de XGBoost:**

<img width="333" height="74" alt="image" src="https://github.com/user-attachments/assets/2a12f1ed-1695-46b0-befb-b232f61a81c9" />

**Conclusiones:**

-	XGBoost fue el mejor modelo con un umbral de 0.40 y un learning rate de 0.05, alcanzando un recall de 0.72.  Ya con todo el flujo tuvo un recall de 0.74 y aplicando cross validation tuvo un recall promedio de 0.73. El modelo es estable con una desviación estándar de 0.012.
-	El tiempo de predicción fue de 0.000008 por dato y el tiempo de entrenamiento es de 1.39 segundos
-	Ni la aplicación de winsorizing o de SMOTE mejoró el modelo.
-	FNN quedó muy por debajo de los modelos clásicos.

**Limitaciones:**

-	Dataset limitado a clientes de Taiwán.
-	Debido a las limitaciones de hardware disponibles, no se realizó una búsqueda exhaustiva de hiperparámetros mediante GridSearchCV. En su lugar, se llevaron a cabo experimentos dirigidos sobre los parámetros con mayor impacto: learning rate, técnicas de balanceo de clases y ajuste del umbral. Esta estrategia permitió reducir significativamente los tiempos de cómputo.
-	La aplicación procesa archivos CSV con la misma estructura que el dataset original.

**Aplicación utilizable en línea:**

Se puede acceder a la aplicación desde esta dirección: https://predicci-n-de-impagos-de-tarjetas-de-cr-dito-2osxkhbxby5n5ip4w.streamlit.app/
