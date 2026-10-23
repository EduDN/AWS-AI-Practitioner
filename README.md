# AWS AI Practitioner — Apuntes de Estudio

> Guía de repaso para la certificación **AWS Certified AI Practitioner**, con definiciones ampliadas, tablas comparativas y el detalle técnico

---

## 1. Inferencia (Inferencing)

Es el proceso de **utilizar un modelo ya entrenado** para generar predicciones o tomar decisiones sobre datos nuevos (no vistos durante el entrenamiento).

| Modo de inferencia | Latencia / Prioridad | Caso de uso típico |
|---|---|---|
| **Batch inferencing** | Alta latencia aceptable | Procesar grandes volúmenes de datos donde no se necesita una respuesta inmediata. |
| **Real-time inferencing** | Latencia mínima (crítica) | Aplicaciones interactivas donde la respuesta debe ser instantánea (chatbots, apps móviles). |
| **Asíncrona (Asynchronous)** | Retraso moderado aceptable | Cargas de trabajo grandes que no requieren resultados inmediatos, pero sí una respuesta procesada eventualmente (ej. payloads pesados). |
| **Serverless inference** | Baja latencia, con posible "cold start" | Tráfico impredecible o solicitudes esporádicas; escala automáticamente según la demanda sin necesidad de gestionar infraestructura. |

---

## 2. Ciclo de Vida de un Modelo Fundacional (FM Lifecycle)

El ciclo de vida completo de un **Foundation Model (FM)** dentro de AWS sigue estas etapas:

1. **Data selection** — selección y preparación de los datos relevantes para el caso de uso.
2. **Optimization** — ajuste del modelo mediante técnicas como **RAG** (*Retrieval-Augmented Generation*) o **Fine-Tuning**.
3. **Evaluation** — medición del desempeño del modelo utilizando **benchmarks** estandarizados.
4. **Deployment** — puesta en producción del modelo para su consumo.
5. **Feedback and continuous improvement** — recolección de retroalimentación real de uso para iterar y mejorar el modelo de forma continua.

---

## 3. Modelos de Difusión (Diffusion Models)

Arquitectura generativa utilizada principalmente para la creación de imágenes, que funciona en dos fases:

- **Forward diffusion** — se introduce progresivamente ruido en una imagen de entrada, paso a paso, hasta que la imagen original queda completamente convertida en ruido puro.
- **Reverse diffusion** — proceso inverso: el modelo aprende a **eliminar el ruido gradualmente** a partir de ruido puro, hasta reconstruir/generar una nueva imagen coherente.

---

## 4. Servicios de IA / ML en AWS

| Servicio | Función |
|---|---|
| **Amazon Polly** | Text to Speech |
| **Amazon Transcribe** | Speech to Text |
| **Amazon Lex** | Construcción de chatbots y agentes conversacionales |
| **Amazon DeepRacer** | Plataforma educativa de **Reinforcement Learning** |
| **Amazon Comprehend** | Extracción de información y análisis de texto (NLP) |

### Jerarquía de servicios de AWS AI/ML

```
Generative AI       → Amazon SageMaker JumpStart, Amazon Bedrock, Amazon Q, Amazon Q Developer
AI/ML services       → Text/Docs: Comprehend, Translate, Textract
                        Vision: Rekognition
                        Search: Kendra
                        Chatbots: Lex
                        Speech: Polly, Transcribe
                        Recommendations: Personalize
                        Misc: DeepRacer
ML frameworks        → Amazon SageMaker
```

Esta pirámide resume el stack de IA de AWS: en la base están los **frameworks de ML** (SageMaker), en el medio los **servicios de IA/ML preentrenados** organizados por dominio, y en la cima los **servicios de IA generativa**.

---

## 5. Aprendizaje Supervisado (Supervised Learning)

- **Classification** — asigna etiquetas o categorías discretas a nuevas instancias de datos no vistas previamente, con base en un modelo previamente entrenado con datos etiquetados.
- **Regression** — predice valores continuos o numéricos a partir de una o más variables de entrada (ej. predecir un precio o una temperatura).

## 6. Aprendizaje No Supervisado (Unsupervised Learning)

- **Clustering** — agrupa los datos en distintos clústeres según similitud de características o distancias, sin necesidad de etiquetas previas.
- **Dimensionality reduction** (reducción de dimensionalidad) — reduce el número de características/variables de un conjunto de datos, eliminando aquellas que no aportan información útil o que introducen ruido, sin perder la esencia de los datos.

---

## 7. Métricas de Negocio para IA Generativa

Indicadores clave para medir el **impacto de negocio** (no solo el desempeño técnico) de una solución de IA generativa:

- **User satisfaction** — satisfacción reportada por los usuarios finales.
- **Average revenue per user (ARPU)** — ingreso promedio generado por usuario.
- **Cross-domain performance** — consistencia del desempeño del modelo across distintos dominios o tipos de tareas.
- **Conversion rate** — tasa de conversión de usuarios hacia una acción deseada.
- **Efficiency** — eficiencia operativa/costo de la solución en relación con el valor entregado.

---

## 8. Prácticas de IA Responsable (Responsible AI)

La IA responsable debe integrarse en **todo el ciclo de vida** de la solución, no solo al final:

**Design → Development → Deployment → Monitoring → Evaluation**

Cada etapa aporta controles distintos: el diseño define principios éticos y de gobernanza; el desarrollo incorpora pruebas de sesgo; el despliegue valida seguridad y cumplimiento; el monitoreo detecta desviaciones en producción; y la evaluación retroalimenta mejoras continuas.

---

## 9. Desafíos en IA: Sesgo y Varianza

- **Bias (sesgo)** — ocurre cuando al modelo le faltan características importantes o los datos de entrenamiento son demasiado simples/limitados para capturar la complejidad real del problema. Se mide como la **diferencia entre las predicciones esperadas del modelo y los valores reales** que se intentan predecir. Un modelo con alto sesgo tiende al **underfitting**.
- **Variance (varianza)** — mide la **sensibilidad del modelo al ruido o a fluctuaciones** en los datos de entrenamiento. Un modelo con alta varianza "memoriza" los datos vistos y es incapaz de generalizar a ejemplos nuevos (**overfitting**).

### Técnicas para manejar sesgo y varianza

| Técnica | Descripción |
|---|---|
| **Validación cruzada (Cross-validation)** | Divide los datos en múltiples particiones de entrenamiento/prueba para obtener una estimación más robusta del desempeño real del modelo. |
| **Aumento de datos (Data augmentation)** | Genera variaciones artificiales de los datos existentes para enriquecer el conjunto de entrenamiento. |
| **Regularización (Regularization)** | Penaliza los valores de peso extremos en modelos lineales, evitando que se sobreajusten a los ejemplos de entrenamiento. |
| **Reducción de dimensiones** | Reduce la cantidad de características de un conjunto de datos, conservando la mayor cantidad de información posible, para simplificar el modelo y evitar el sobreajuste. |

---

## 10. Desarrollo Responsable de IA con Amazon SageMaker

| Herramienta | Función |
|---|---|
| **SageMaker Clarify** | Detecta y ayuda a gestionar **sesgos** en modelos de ML, y explica cómo el modelo llega a sus predicciones. |
| **SageMaker Data Wrangler** | Aplica **submuestreo aleatorio**, **sobremuestreo aleatorio** y **sobremuestreo minoritario sintético (SMOTE)** para reequilibrar conjuntos de datos desbalanceados. |
| **SageMaker Experiments** | Permite **crear, administrar, analizar y comparar** experimentos de machine learning de forma organizada. |
| **SageMaker Model Monitor** | Configura **alertas automáticas** que notifican cuando se detectan desviaciones en la calidad de un modelo en producción. |
| **SageMaker Role Manager** | Permite a los administradores **definir permisos mínimos** (principio de mínimo privilegio) en cuestión de minutos. |
| **SageMaker Model Cards** | Captura, recupera y comparte información esencial del modelo (usos previstos, clasificación de riesgos, detalles de entrenamiento) desde su concepción hasta su despliegue. |
| **SageMaker Model Dashboard** | Permite **rastrear qué modelos están desplegados para inferencia**, si se usan en trabajos de transformación por lotes o alojados en endpoints, y monitorear su desempeño en predicciones en tiempo real sobre datos en vivo. |

---

## 11. Procesamiento Inteligente de Documentos (IDP)

**IDP (Intelligent Document Processing)** — conjunto de tecnologías (OCR + NLP + ML) que permiten extraer, clasificar y comprender automáticamente información contenida en documentos no estructurados o semi-estructurados (facturas, contratos, formularios).

---

## 12. Fine-Tuning (Ajuste Fino de Modelos)

- **Supervised fine-tuning** — utiliza **datos etiquetados** para ajustar los parámetros del modelo hacia una tarea específica.
- **Reinforcement fine-tuning** — se basa en **retroalimentación (función de recompensa)**:
  - **Tareas objetivas** — la recompensa puede calcularse automáticamente (ej. mediante una función en **AWS Lambda**).
  - **Tareas subjetivas** — se utiliza **otro modelo como "juez"**, al cual se le proporcionan instrucciones de evaluación para calificar las respuestas.
- **Domain Adaptation Fine-Tuning** — ajusta los parámetros del modelo utilizando **datos específicos de un dominio**, mejorando su desempeño en ese contexto particular.
- **Continued Pre-Training** — entrena aún más el modelo base con un **gran corpus de datos específicos del dominio** (sin etiquetar), mejorando su capacidad de comprender términos, jerga y contexto propios de ese dominio.

> **Diferencia clave para el examen:** *Continued pre-training* utiliza datos **sin etiquetar (unlabeled)** para preentrenar el modelo, mientras que el *fine-tuning* utiliza datos **etiquetados (labeled)** para entrenarlo hacia una tarea concreta.

---

## 13. Distillation y Quantization

- **Distillation (Destilación de conocimiento)** — técnica que entrena un modelo más pequeño ("estudiante") para replicar el comportamiento de un modelo más grande ("maestro"), logrando modelos **más pequeños y rápidos** con una pérdida mínima de desempeño.
- **Quantization (Cuantización)** — reduce la precisión numérica de los pesos de un LLM (por ejemplo, de 32 bits a 8 bits), disminuyendo el tamaño del modelo y acelerando la inferencia, a cambio de una posible ligera pérdida de precisión.

---

## 14. Evaluación de Modelos con Amazon Bedrock

Bedrock ofrece dos enfoques principales para evaluar un modelo fundacional (FM):

### a) Evaluación automática (Automatic evaluation)
- **Programmatic** — evaluación a través de **métricas cuantitativas del modelo**.
- **LLM como juzgador (LLM-as-a-judge)** — se emplea otro LLM para calificar las respuestas generadas.

**Flujo:** *Benchmark Questions* → se envían tanto al conjunto de *Benchmark Answers* (respuestas de referencia) como al *Model to Evaluate*, que genera sus propias *Generated Answers*. Ambas respuestas (referencia y generada) se comparan mediante un **Judge Model**, que produce un **Grading Score** final.

### b) Evaluación humana (Human evaluation)
Sigue el mismo flujo, pero en lugar de un modelo juzgador, un **equipo de trabajo (Employees / Work Team)** revisa manualmente las respuestas generadas frente a las respuestas de referencia y asigna la calificación (*Grading Score*).

---

## 15. Métricas Automatizadas para Evaluar un FM

| Métrica | Uso |
|---|---|
| **ROUGE** | Evalúa tareas de **resumen (summarization)** y traducción automática, midiendo la superposición de n-gramas entre el texto generado y el de referencia. |
| **BLEU** (*Bilingual Evaluation Understudy*) | Evalúa la calidad de **traducciones automáticas**; tiende a **penalizar en exceso las respuestas demasiado breves**. |
| **BERTScore** | Compara la **similitud semántica (coseno)** entre embeddings del texto generado y el de referencia, capturando significado más allá de la coincidencia literal de palabras. |
| **Perplexity** | Evalúa **qué tan bien predice el modelo el siguiente token**; a menor perplejidad, mejor capacidad predictiva del modelo sobre el texto. |

### Métricas de negocio para evaluar un modelo
- User satisfaction
- Media de revenue por usuario (ARPU)
- Rendimiento entre dominios (cross-domain performance)
- Eficiencia (efficiency)

---

## 16. Bases de Datos Vectoriales en AWS

| Servicio | Descripción |
|---|---|
| **Amazon OpenSearch Service** (Serverless y Clúster Administrado) | Base de datos de búsqueda y análisis; permite consultas de similitud en tiempo real, almacena millones de **embeddings** vectoriales, con gestión de índices escalable y búsqueda rápida del **vecino más cercano (kNN)**. |
| **Amazon Aurora PostgreSQL** | Base de datos relacional, propietaria de AWS, con soporte de extensiones vectoriales (pgvector). |
| **Amazon Neptune Analytics** | Base de datos de **grafos** que permite análisis de grafos de alto rendimiento y soluciones RAG basadas en grafos (**GraphRAG**). |
| **Amazon S3 Vectors** | Almacenamiento **rentable y duradero** para vectores, con rendimiento de consulta en subsegundos. |

---

## 17. Monitoreo con Amazon CloudWatch

- Utilizado para **monitorear** el comportamiento de los modelos y servicios de IA desplegados.
- **Model Invocation Logging** — registra el detalle de cada invocación realizada a un modelo (entradas, salidas, metadatos), útil para auditoría, depuración y cumplimiento normativo.

---

## 18. Modelos de Precios (Pricing)

### Modalidades generales
- **On demand (bajo demanda)**
- **Batch (por lotes)**
- **Provisioned (aprovisionado)**

### Amazon Bedrock — Precios en detalle

| Modalidad | Detalle |
|---|---|
| **Bajo demanda** | Pago por uso, sin compromiso. Modelos de texto: se cobra por cada token de entrada/salida procesado. Modelos de incrustación (embeddings): se cobra por cada token de entrada procesado. Modelos de imagen: se cobra por cada imagen generada. Compatible con modelos base y modelos personalizados. |
| **Lotes (Batch)** | Permite procesar múltiples predicciones a la vez; la salida se entrega como un único archivo en **Amazon S3**. Puede ofrecer **descuentos de hasta el 50%** frente al modo bajo demanda. |
| **Rendimiento aprovisionado (Provisioned Throughput)** | Se compran unidades de modelo por un período determinado (1 mes, 6 meses, etc.). El "rendimiento" se define como el número máximo de tokens de entrada/salida procesados por minuto. Compatible con modelos base, afinados (fine-tuned) y personalizados. |

---

## 19. Otros Servicios Relevantes de AWS

- **Amazon Nova** — familia de modelos fundacionales multimodales desarrollados por AWS, integrados en Amazon Bedrock.
- **AWS Q** — asistente de IA generativa de AWS, con integraciones específicas:
  - **AWS Q para chatbots** — permite poner a disposición del usuario un asistente de Amazon Q integrado en herramientas como **Microsoft Teams** o **Slack**.
  - **AWS Q para Glue** — asistencia inteligente dentro de procesos **ETL** (Extract, Transform, Load).
  - **AWS Q para QuickSight** — permite **crear dashboards y realizar consultas en lenguaje natural** sobre los propios datos de negocio.
- **AWS MLflow en Amazon SageMaker** — permite usar **MLflow** junto con SageMaker para **rastrear, organizar, visualizar, analizar y comparar** experimentos iterativos de ML, obteniendo insights comparativos y registrando/desplegando los modelos con mejor desempeño.

---

## 20. Algoritmos y Métricas para Evaluar un Modelo de ML

| Métrica | Uso |
|---|---|
| **Confusion Matrix** | Evalúa el desempeño de modelos de **clasificación**, mostrando verdaderos positivos, verdaderos negativos, falsos positivos y falsos negativos. |
| **RMSE** (*Root Mean Squared Error*) | Mide el **error promedio** en modelos de **regresión**, penalizando más los errores grandes. |
| **MAE** (*Mean Absolute Error*) | Mide la **magnitud promedio de los errores** en un conjunto de predicciones, sin considerar su dirección (sobre o subestimación). |
| **Correlation Matrix** | Mide la **correlación estadística** entre distintas variables o características de un conjunto de datos; se usa típicamente para comprender relaciones entre variables continuas. |

---

## 21. Amazon Forecast

Servicio de ML especializado en **series temporales**. A diferencia de los modelos convencionales, los datos aquí **dependen del tiempo** y presentan patrones característicos como **tendencias** o **estacionalidad**, que el servicio modela automáticamente para generar predicciones futuras.

---

## 22. Infraestructura Global de AWS

- **Cada Availability Zone (AZ)** está compuesta por **uno o más centros de datos discretos**.
- **Cada Región de AWS** consiste en un **mínimo de tres Zonas de Disponibilidad (AZ)**.

Este diseño garantiza redundancia y alta disponibilidad: si una AZ falla, las otras dentro de la misma región pueden continuar operando.

---

## 23. Explicabilidad de Modelos: Shapley Values y PDP

- **Shapley values** — ofrecen una **explicación local**, cuantificando la contribución específica de **cada característica** a la predicción de **una instancia particular**. Se usan para **explicar predicciones individuales**.
- **Partial Dependence Plots (PDP)** — ofrecen una **explicación global**, mostrando el **efecto marginal** de una característica sobre las predicciones del modelo **a través de todo el conjunto de datos**. Se usan para **comprender el comportamiento del modelo a nivel de dataset completo**.

> **Regla práctica:** Shapley = explicación individual (por predicción). PDP = explicación global (por dataset).

---

## 24. Herramientas de Etiquetado y Explicabilidad en SageMaker

- **Amazon SageMaker Ground Truth** — para entrenar un modelo de ML se requiere un conjunto de datos **grande, de alta calidad y etiquetado**; Ground Truth está diseñado específicamente para **crear estos datasets etiquetados**, combinando **etiquetado automatizado y humano**.
- **Amazon SageMaker Clarify** — provee herramientas para **explicar cómo los modelos de ML llegan a sus predicciones**, además de detectar sesgos.

---

## 25. Tipos de Sesgo (Bias)

| Tipo de sesgo | Descripción |
|---|---|
| **Sampling bias** | Ocurre cuando los **datos usados para entrenar el modelo no reflejan fielmente** la población o el escenario real al que se aplicará el modelo. |
| **Measurement bias** | Imprecisiones en la **recopilación de datos**, como equipos defectuosos o procesos de medición inconsistentes. |
| **Observer bias** | Errores humanos o **subjetividad** introducidos durante el análisis o la observación de los datos. |
| **Confirmation bias** | Implica **buscar o interpretar información de forma selectiva** para confirmar creencias o hipótesis preexistentes. |

---

## 26. Gobernanza, Cumplimiento y Seguridad en AWS

- **AWS Trusted Advisor** — optimiza el entorno de AWS en áreas como **ahorro de costos, rendimiento, seguridad y tolerancia a fallos**; es una herramienta esencial para la **gobernanza** en sistemas de IA.
- **AWS Audit Manager** — automatiza la recopilación de evidencia para facilitar auditorías de riesgo y cumplimiento normativo continuo.
- **Amazon Inspector** — servicio automatizado de **evaluación de seguridad** que mejora la seguridad y el cumplimiento de las aplicaciones desplegadas en AWS, evaluando exposición, vulnerabilidades y desviaciones de buenas prácticas.
- **AWS Artifact** — permite a los usuarios **recibir notificaciones** cuando hay nuevos documentos o reportes de cumplimiento disponibles, incluyendo reportes de cumplimiento de ISV (proveedores de software independientes).

### Data residency vs. Data retention
- **Data residency** — se refiere a la **ubicación física** donde se almacenan los datos.
- **Data retention** — define las **políticas de cuánto tiempo** deben almacenarse y mantenerse los datos.

---

## 27. Continued Pre-training vs. Fine-Tuning (resumen para examen)

| Técnica | Tipo de datos requeridos | Objetivo |
|---|---|---|
| **Continued pre-training** | Datos **sin etiquetar (unlabeled)** | Ampliar el conocimiento general del modelo en un dominio específico. |
| **Fine-tuning** | Datos **etiquetados (labeled)** | Especializar al modelo en una tarea concreta y bien definida. |

---

## 28. Otras Herramientas Clave de Amazon SageMaker y AWS

| Herramienta | Función |
|---|---|
| **Amazon SageMaker Feature Store** | Repositorio **totalmente administrado y de propósito específico** para almacenar, compartir y gestionar *features* (características) usadas como entradas en modelos de ML, tanto durante el entrenamiento como en la inferencia. |
| **Amazon SageMaker Canvas** | Permite crear modelos de machine learning **altamente precisos sin experiencia previa en ML ni escribir una sola línea de código** (interfaz visual/no-code). |
| **Amazon Augmented AI (Amazon A2I)** | Permite implementar **flujos de trabajo de revisión humana** sobre las predicciones generadas por modelos de machine learning. |
| **Amazon Mechanical Turk** | Provee un **marketplace para externalizar tareas** (como etiquetado de datos) a una fuerza de trabajo distribuida y humana. |

> **Diferencia clave:** *Ground Truth* está diseñado **específicamente** para crear datasets etiquetados de ML (combinando automatización + humanos), mientras que *Mechanical Turk* es un marketplace **más general** para externalizar cualquier tipo de tarea a trabajadores humanos.

---

## 29. Feature Engineering

Consiste en **seleccionar, modificar o crear características (features)** a partir de datos crudos, con el objetivo de mejorar el desempeño de los modelos de machine learning. Es un paso crítico porque puede **incrementar significativamente la precisión y la eficiencia** del modelo resultante.

---

## 30. Tipos de Aprendizaje Adicionales

- **Semi-supervised learning (aprendizaje semi-supervisado)** — combina una pequeña cantidad de datos **etiquetados** con una gran cantidad de datos **no etiquetados**, aprovechando ambos para mejorar el entrenamiento del modelo cuando el etiquetado manual es costoso o limitado.

---

## 31. Tipos de Despliegue (Deployment) en SageMaker

| Tipo de Inferencia | Latencia | Tamaño de Payload | Tiempo de Procesamiento | Caso de Uso |
|---|---|---|---|---|
| **Real-time Inference** | Baja (milisegundos a segundos) | Hasta 25 MB (un registro) | Máx. 60 segundos | Predicciones rápidas, casi instantáneas, para aplicaciones web/móviles. |
| **Serverless Inference** | Baja (milisegundos a segundos) | Hasta 4 MB (un registro) | Máx. 60 segundos | Inferencia esporádica y de corto plazo sin gestionar infraestructura; tolera *cold starts*. |
| **Asynchronous Inference** | Media a alta ("casi tiempo real") | Hasta 1 GB (un registro) | Máx. 1 hora | Payloads grandes y cargas de trabajo que requieren tiempos de procesamiento más largos. |
| **Batch Transform** | Alta (minutos a horas) | Hasta 100 MB por invocación (por mini-lote) | Máx. 1 hora | Procesamiento masivo de grandes datasets; procesamiento concurrente. |

---

## Resumen de Equivalencias Conceptuales

| Concepto | Servicio/Herramienta clave en AWS |
|---|---|
| Text to Speech | Amazon Polly |
| Speech to Text | Amazon Transcribe |
| Chatbots | Amazon Lex |
| Reinforcement Learning (educativo) | Amazon DeepRacer |
| Extracción y análisis de texto (NLP) | Amazon Comprehend |
| Etiquetado de datos (labeled datasets) | Amazon SageMaker Ground Truth |
| Externalización de tareas humanas | Amazon Mechanical Turk |
| Explicabilidad de modelos | Amazon SageMaker Clarify |
| Revisión humana de predicciones | Amazon Augmented AI (A2I) |
| Series temporales | Amazon Forecast |
| Gobernanza y optimización de costos | AWS Trusted Advisor |
| Evaluación de seguridad automatizada | Amazon Inspector |
| Notificaciones de cumplimiento | AWS Artifact |
