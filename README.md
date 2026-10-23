# Hackathon 2: Agente de WhatsApp con Llama

Agente conversacional para el manejo integrado de *Blattella germanica*, desarrollado como proyecto del Módulo 2 de **IA Aplicada a Modelos Abiertos**.

## Objetivo

Construir un agente basado en Llama, conectado a WhatsApp, que oriente al usuario en el monitoreo y manejo integrado de *Blattella germanica* mediante consultas en lenguaje natural.

El agente permite evaluar registros de capturas y proporcionar recomendaciones de manejo cultural, físico y orientación general sobre manejo químico.

## Arquitectura

El agente integra cinco componentes:

- **Llama 3.1 y Llama Stack:** generan respuestas y gestionan la interacción conversacional.
- **Memoria conversacional:** conserva el contexto de los mensajes durante la sesión.
- **Function calling:** ejecuta una función para clasificar el nivel de infestación según las capturas registradas.
- **RAG:** recupera información de una guía didáctica de manejo integrado.
- **Llama Guard y Prompt Guard:** filtran contenido problemático y detectan intentos de inyección de instrucciones.

La comunicación se realiza mediante WhatsApp Cloud API, utilizando FastAPI y ngrok para conectar temporalmente el agente con WhatsApp.

## Evaluación

Se realizaron pruebas mediante WhatsApp para verificar el monitoreo, las recomendaciones, la memoria conversacional y los mecanismos de seguridad.

En la ejecución registrada:

| Indicador | Resultado |
|---|---|
| Mensajes procesados | 13 |
| Tiempo promedio de respuesta | 13.6 s |
| Tasa de error | 15.4 % |

El agente clasificó correctamente el escenario de ocho capturas durante siete días como infestación moderada. Prompt Guard bloqueó un intento de inyección de instrucciones y Llama Guard bloqueó una consulta peligrosa.

Se identificaron respuestas imprecisas y una exposición de información interna de una función, por lo que el prototipo requiere mejoras antes de su utilización en producción.

## Ejecución

El proyecto está contenido en el notebook:

`Agente_WhatsApp_MIP_Blattella_germanica.ipynb`

Para ejecutarlo en Google Colab se requiere configurar las credenciales de WhatsApp Cloud API y Hugging Face mediante Colab Secrets, instalar las dependencias y ejecutar secuencialmente las celdas.

Las versiones de las bibliotecas utilizadas se encuentran en `requirements.txt`.

## Alcance y limitaciones

El proyecto es un prototipo educativo que utiliza umbrales didácticos de clasificación de infestaciones, sin validación para aplicaciones profesionales.

La conexión mediante ngrok es temporal y la persistencia de la memoria después de reiniciar Colab no ha sido verificada.

El agente demuestra la integración de WhatsApp, modelos abiertos, memoria, recuperación de información, llamadas a funciones, seguridad y monitoreo básico.
