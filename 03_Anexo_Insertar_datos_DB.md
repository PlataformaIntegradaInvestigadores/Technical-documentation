# Documentación Técnica para Acceder a la Base de Datos PostgreSQL en Docker

Esta guía describe los pasos para acceder a la base de datos PostgreSQL ejecutándose en un contenedor Docker desde la línea de comandos, e incluye los comandos necesarios para acceder al terminal de Docker y conectar a la base de datos PostgreSQL.



#### Paso Previo: Identificar el Contenedor de la Base de Datos

Antes de poder acceder al contenedor que ejecuta PostgreSQL, necesitas saber el nombre o ID exacto del contenedor. Para identificar el contenedor, sigue estos pasos:

1. **Listar todos los contenedores en ejecución:**
   Utiliza el siguiente comando para ver todos los contenedores Docker que están actualmente en ejecución:
   ```bash
   docker ps
   ```
   Este comando mostrará una lista de todos los contenedores activos, incluyendo nombres, IDs, imágenes usadas, y más.

2. **Identificar el contenedor de la base de datos:**
   Busca en la lista el contenedor que está usando la imagen de PostgreSQL. Normalmente podrás identificarlo por el nombre de la imagen (por ejemplo, `postgres`) y por los nombres personalizados que podrías haber asignado durante la configuración del `docker-compose`.


#### 1. Acceso al Terminal del Contenedor Docker
En esta guia se toma de base que el nombre de la BD es social_consensus_backend-db-1, necesitas acceder al contenedor Docker que ejecuta la base de datos PostgreSQL. Utiliza el siguiente comando en la línea de comandos para ingresar al terminal del contenedor Docker donde está corriendo PostgreSQL:

```bash
docker exec -it social_consensus_backend-db-1 bash
```

Este comando te permitirá acceder al bash del contenedor Docker cuyo nombre es `social_consensus_backend-db-1`.

#### 2. Conectar a PostgreSQL usando psql
Una vez dentro del contenedor, el siguiente paso es conectarse a la base de datos PostgreSQL utilizando `psql`, el cliente de línea de comandos de PostgreSQL. Para mantener la seguridad, es importante no exponer directamente las credenciales en la documentación. Asegúrate de utilizar las credenciales que has definido en tu archivo `.env`. Aquí te muestro cómo conectarte utilizando variables de entorno:

```bash
psql -U $DB_USER -d $DB_NAME
```

Este comando inicia `psql` y se conecta a la base de datos usando las variables de entorno `DB_USER` y `DB_NAME`, las cuales deben estar definidas previamente en tu archivo `.env`.

#### 3. Trabajo dentro de PostgreSQL
Después de acceder a `psql`, puedes ejecutar cualquier comando SQL para interactuar con la base de datos. Por ejemplo, para insertar una gran cantidad de temas, primero puedes limpiar la tabla si es necesario:

```sql
TRUNCATE TABLE "concensus_recommendedtopic" CASCADE;
```

Luego, para insertar los temas:

```sql
INSERT INTO concensus_recommendedtopic (topic_name, group_id) VALUES
('Quantum Computing Algorithms', NULL),
('AI in Drug Discovery', NULL),
('AI in Healthcare Monitoring Systems', NULL),
('Data Mining in Social Networks', NULL),
('Deep Learning for Image Recognition', NULL),
('AI in Predictive Maintenance', NULL),
('AI in Financial Forecasting', NULL),
('AI in Environmental Impact Assessment', NULL),
('Adaptive Learning Technologies', NULL),
('AI in Autonomous Drone Navigation', NULL),
('AI in Healthcare Treatment Planning', NULL),
('AI in Smart Grid Analytics', NULL),
('Cybersecurity Threat Detection', NULL),
('AI in Predictive Maintenance for Manufacturing', NULL),
('Smart Cities and Urban Computing', NULL),
('Automation of Neural Network Design', NULL),
('AI in Smart Home Automation', NULL),
('Cloud Security and Compliance', NULL),
('Digital Twin Technologies', NULL),
('AI in Smart City Infrastructure', NULL),
('AI in Real-Time Social Media Monitoring', NULL),
('AI in Personalized User Experiences', NULL),
('AI in Personalized Travel Recommendations', NULL),
('Wearable Technology in Healthcare', NULL),
('AI in Sports Performance Analysis', NULL),
('AI in Renewable Energy Management', NULL),
('AI in Healthcare Diagnostics', NULL),
('AI in Autonomous Warehouse Management', NULL),
('AI in Dynamic Pricing Strategies', NULL),
('Virtual Reality in Education', NULL),
('AI in Real-Time Energy Optimization', NULL),
('AI in Financial Market Prediction', NULL),
('Sensor Networks for Environmental Monitoring', NULL),
('Blockchain for Secure Data Transactions', NULL),
('Mobile Health Technologies', NULL),
('AI in Talent Acquisition', NULL),
('AI in Legal Document Analysis', NULL),
('AI in Smart Contract Development', NULL),
('Autonomous Vehicle Navigation', NULL),
('AI in Natural Disaster Management', NULL),
('AI in Automated Legal Research', NULL),
('AI in Supply Chain Risk Management', NULL),
('AI in Environmental Sustainability', NULL),
('Development of Contextual Recommendation Systems', NULL),
('Interpretability and Explainability of AI Models', NULL),
('AI in Predictive Policing', NULL),
('Cyber-Physical Systems Security', NULL),
('AI in Autonomous Maritime Navigation', NULL),
('AI in Automated Customer Support', NULL),
('Natural Language Processing in Healthcare', NULL),
('AI in Real-Time Language Translation', NULL),
('Computational Neuroscience', NULL),
('AI in Real-Time Sports Analytics', NULL),
('AI in Real-Time Market Analysis', NULL),
('Renewable Energy Optimization', NULL),
('Sentiment Analysis in Social Media', NULL),
('AI in Real-Time Fraud Prevention', NULL),
('Machine Learning in Financial Fraud Detection', NULL),
('AI in E-commerce Personalization', NULL),
('AI in Customer Service Automation', NULL),
('AI in Financial Risk Management', NULL),
('Personalized Learning Environments', NULL),
('Human-Computer Interaction Innovations', NULL),
('Evolutionary Computation Techniques', NULL),
('AI in Personalized Content Delivery', NULL),
('Edge Computing for IoT', NULL),
('Bioinformatics and Genomic Data Analysis', NULL),
('AI in Agriculture Yield Prediction', NULL),
('AI in Cybersecurity Incident Response', NULL),
('AI in Personalized Medicine', NULL),
('Cognitive Computing in Robotics', NULL),
('AI Ethics and Governance', NULL),
('Semantic Web and Ontologies', NULL),
('AI-Driven Supply Chain Optimization', NULL),
('Privacy-Enhancing Technologies', NULL),
('AI in Autonomous Retail Checkout', NULL),
('Big Data Analytics in Retail', NULL),
('AI in Autonomous Logistics', NULL),
('Intelligent Transportation Systems', NULL),
('AI in Employee Performance Management', NULL),
('Smart Grid Technologies', NULL),
('AI in Personalized Fitness Training', NULL),
('AI in Real-Time Traffic Management', NULL),
('Augmented Reality in Industrial Training', NULL),
('AI in Dynamic Content Generation', NULL),
('AI in Dynamic Supply Chain Optimization', NULL),
('Internet of Medical Things', NULL),
('Predictive Analytics in Business', NULL),
('AI in Human Resource Management', NULL),
('AI in Predictive Analytics for Healthcare', NULL),
('AI in Real-Time Fraud Detection', NULL),
('AI in Content Recommendation', NULL),
('High-Performance Computing Applications', NULL),
('AI in Precision Agriculture', NULL),
('AI in Smart Building Management', NULL),
('AI in Personalized Marketing', NULL),
('AI in Customer Sentiment Analysis', NULL),
('AI in Retail Inventory Management', NULL),
('Computer Vision Applications in Agriculture', NULL),
('Machine Translation and Multilingual NLP', NULL),
('AI in Drug Discovery', NULL),
('AI in Healthcare Monitoring Systems', NULL),
('Data Mining in Social Networks', NULL),
('Deep Learning for Image Recognition', NULL),
('AI in Predictive Maintenance', NULL),
('AI in Financial Forecasting', NULL),
('AI in Environmental Impact Assessment', NULL),
('Adaptive Learning Technologies', NULL),
('AI in Autonomous Drone Navigation', NULL),
('AI in Healthcare Treatment Planning', NULL),
('AI in Smart Grid Analytics', NULL),
('Cybersecurity Threat Detection', NULL),
('AI in Predictive Maintenance for Manufacturing', NULL),
('Smart Cities and Urban Computing', NULL),
('Automation of Neural Network Design', NULL),
('AI in Smart Home Automation', NULL),
('Cloud Security and Compliance', NULL),
('Digital Twin Technologies', NULL),
('AI in Smart City Infrastructure', NULL),
('AI in Real-Time Social Media Monitoring', NULL),
('AI in Personalized User Experiences', NULL),
('AI in Personalized Travel Recommendations', NULL),
('Wearable Technology in Healthcare', NULL),
('AI in Sports Performance Analysis', NULL),
('AI in Renewable Energy Management', NULL),
('AI in Healthcare Diagnostics', NULL),
('AI in Autonomous Warehouse Management', NULL),
('AI in Dynamic Pricing Strategies', NULL),
('Virtual Reality in Education', NULL),
('AI in Real-Time Energy Optimization', NULL),
('AI in Financial Market Prediction', NULL),
('Sensor Networks for Environmental Monitoring', NULL),
('Blockchain for Secure Data Transactions', NULL),
('Mobile Health Technologies', NULL),
('AI in Talent Acquisition', NULL),
('AI in Legal Document Analysis', NULL),
('AI in Smart Contract Development', NULL),
('Autonomous Vehicle Navigation', NULL),
('AI in Natural Disaster Management', NULL),
('AI in Automated Legal Research', NULL),
('AI in Supply Chain Risk Management', NULL),
('AI in Environmental Sustainability', NULL),
('Development of Contextual Recommendation Systems', NULL),
('Interpretability and Explainability of AI Models', NULL),
('AI in Predictive Policing', NULL),
('Cyber-Physical Systems Security', NULL),
('AI in Autonomous Maritime Navigation', NULL),
('AI in Automated Customer Support', NULL),
('Natural Language Processing in Healthcare', NULL),
('AI in Real-Time Language Translation', NULL),
('Computational Neuroscience', NULL),
('AI in Real-Time Sports Analytics', NULL),
('AI in Real-Time Market Analysis', NULL),
('Renewable Energy Optimization', NULL),
('Sentiment Analysis in Social Media', NULL),
('AI in Real-Time Fraud Prevention', NULL),
('Machine Learning in Financial Fraud Detection', NULL),
('AI in E-commerce Personalization', NULL),
('AI in Customer Service Automation', NULL),
('AI in Financial Risk Management', NULL),
('Personalized Learning Environments', NULL),
('Human-Computer Interaction Innovations', NULL),
('Evolutionary Computation Techniques', NULL),
('AI in Personalized Content Delivery', NULL),
('Edge Computing for IoT', NULL),
('Bioinformatics and Genomic Data Analysis', NULL),
('AI in Agriculture Yield Prediction', NULL),
('AI in Cybersecurity Incident Response', NULL),
('AI in Personalized Medicine', NULL),
('Cognitive Computing in Robotics', NULL),
('AI Ethics and Governance', NULL),
('Semantic Web and Ontologies', NULL),
('AI-Driven Supply Chain Optimization', NULL),
('Privacy-Enhancing Technologies', NULL),
('AI in Autonomous Retail Checkout', NULL),
('Big Data Analytics in Retail', NULL),
('AI in Autonomous Logistics', NULL),
('Intelligent Transportation Systems', NULL),
('AI in Employee Performance Management', NULL),
('Smart Grid Technologies', NULL),
('AI in Personalized Fitness Training', NULL),
('AI in Real-Time Traffic Management', NULL),
('Augmented Reality in Industrial Training', NULL),
('AI in Dynamic Content Generation', NULL),
('AI in Dynamic Supply Chain Optimization', NULL),
('Internet of Medical Things', NULL),
('Predictive Analytics in Business', NULL),
('AI in Human Resource Management', NULL),
('AI in Predictive Analytics for Healthcare', NULL),
('AI in Real-Time Fraud Detection', NULL),
('AI in Content Recommendation', NULL),
('High-Performance Computing Applications', NULL),
('AI in Precision Agriculture', NULL),
('AI in Smart Building Management', NULL),
('AI in Software Architecture', NULL),
('AI in Personalized Marketing', NULL),
('AI in Customer Sentiment Analysis', NULL),
('AI in Retail Inventory Management', NULL),
('Computer Vision Applications in Agriculture', NULL),
('Machine Translation and Multilingual NLP', NULL);
```


#### 4. Salir del Contenedor
Una vez que hayas terminado de trabajar dentro de la base de datos, puedes salir del cliente `psql` con el comando `\q` y luego del contenedor Docker utilizando `exit`.
