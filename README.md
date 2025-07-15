🔍 Inspección Gateway
Inspeccion Gateway es un workflow de GitHub Actions diseñado para realizar una inspección pasiva de la superficie de exposición de un dominio o IP, con un enfoque particular en la detección de Gateways de Seguridad, WAFs, CDNs e Ingresses. Opcionalmente, puede generar un informe detallado y contextualizado utilizando la inteligencia artificial de Google Gemini.

🚀 Uso
Para ejecutar este workflow, navega a la pestaña "Actions" en tu repositorio de GitHub, selecciona "Inspeccion Gateway" en la barra lateral izquierda y haz clic en "Run workflow".

Deberás proporcionar los siguientes inputs:

dominio: El dominio o dirección IP del objetivo a analizar (ej: juice-shop.herokuapp.com).

gemini: Selecciona true si deseas generar un informe avanzado con la IA de Gemini, o false para obtener solo el resumen estándar.

📊 Resultados del Análisis
El workflow siempre realizará una serie de análisis pasivos utilizando herramientas como HTTPX, WhatWeb, Wafw00f y Nmap, y analizará los encabezados HTTP/S y el certificado SSL/TLS. Los resultados se presentarán de dos maneras, dependiendo de tu elección para Gemini:

📋 1. Modo Estándar (Sin Gemini o si Gemini falla)
Si seleccionas gemini: 'false' o si la generación del informe con Gemini encuentra algún problema, el workflow proporcionará un "Resumen de Hallazgos (Checklist Estándar)" directamente en el log de la ejecución de GitHub Actions.

Este checklist está diseñado para darte una visión rápida y concisa de los puntos clave, con un énfasis claro en la seguridad perimetral:

¿Es un Gateway de seguridad (WAF, API Gateway, Ingress, Firewall, Balanceador de Carga)? ✅ / ❌

¿Pasa por Gateway (x-forwarded, headers específicos de proxy/CDN)? ✅ / ❌

¿Tecnología detectada? ✅ / ❌

¿Certificado válido y vigente? ✅ / ⚠️ (Próximo a expirar) / ❌ (Expirado)

¿CVEs encontrados? ✅ / ⚠️

Este formato te permite identificar rápidamente la presencia de componentes de seguridad y el estado general del objetivo.

✨ 2. Modo Potenciado por Gemini AI (Si gemini: 'true' y exitoso)
Cuando activas la opción gemini: 'true' y la integración con la IA de Google Gemini se completa con éxito, el workflow generará un "Análisis Completo y Empoderado por Gemini AI".

Este informe es una versión ampliada y contextualizada del análisis estándar. Gemini actúa como un experto en ciberseguridad, analizando los logs brutos de todas las herramientas para:

Proporcionar un Resumen Ejecutivo conciso.

Detallar la Información General del Objetivo, incluyendo tecnologías, servidor web, CDN/WAF detectado y puertos abiertos.

Ofrecer un Análisis de Certificado SSL/TLS con estado de expiración.

Desglosar el Análisis de Encabezados HTTP/S, destacando headers de seguridad y de proxy/CDN.

Identificar Vulnerabilidades Potenciales y Riesgos basados en las tecnologías y la configuración de seguridad (o su ausencia).

Sugerir Recomendaciones y Próximos Pasos para mejorar la postura de seguridad.

Este informe es ideal para una comprensión más profunda y para la toma de decisiones estratégicas en seguridad.

📦 Artefactos Generados
Al finalizar cada ejecución, el workflow subirá un artefacto llamado inspeccion-gateway-results-{run_id}. Este artefacto contendrá todos los archivos de salida generados por las herramientas, incluyendo:

httpx_output.json

whatweb_output.txt

wafw00f_output.txt

nmap_output.txt

headers_output.txt

cert_output.txt

cve_resultados.txt

gateinspector_raw_logs.txt (el log consolidado de todas las herramientas)

gemini_report.md (solo si se generó el informe de Gemini)

Puedes descargar este artefacto desde la página de resumen de la ejecución del workflow para un análisis offline.

🔑 Requisitos
Para utilizar la funcionalidad de Gemini, debes configurar una API Key de Google Gemini como un secreto de repositorio en GitHub. El secreto debe llamarse GEMINI_API_KEY.
