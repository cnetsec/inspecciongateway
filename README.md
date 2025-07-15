# 🔍 Inspección Gateway

**`Inspeccion Gateway`** es un workflow de GitHub Actions diseñado para realizar una **inspección pasiva de la superficie de exposición** de un dominio o IP, con foco especial en la detección de:

🛡️ **WAFs**, 🌐 **Gateways de Seguridad**, 📦 **CDNs**, y 🛣️ **Ingress Controllers**.

Además, ofrece la opción de generar un informe técnico y ejecutivo **potenciado por IA con Google Gemini**.

---

## 🚀 Cómo usar

1. Accede a la pestaña **"Actions"** de tu repositorio.
2. Selecciona **"Inspeccion Gateway"** en el menú lateral.
3. Haz clic en **"Run workflow"**.
4. Completa los siguientes inputs:

- 🔹 **`dominio`**: El dominio o IP objetivo (ej: `juice-shop.herokuapp.com`)
- 🔹 **`gemini`**: Selecciona `true` para generar un informe avanzado con Gemini AI, o `false` para un análisis estándar.

---

## 📊 Resultados del Análisis

El análisis incluye:

- Detección de tecnologías expuestas
- Verificación de encabezados HTTP/S
- Análisis de certificado SSL/TLS
- Escaneo de puertos básicos
- Detección de gateways de seguridad
- Consulta de CVEs en CIRCL

Los resultados se presentan según la opción de Gemini:

---

### 📋 Modo Estándar (`gemini: false` o en caso de error)

Se genera un **Checklist Estándar** con los siguientes puntos clave:

- ✅ **¿Gateway de Seguridad detectado?**  
- ✅ **¿Headers de proxy/CDN presentes?**  
- ✅ **¿Tecnología identificada (HTTPX / WhatWeb)?**  
- ✅ / ⚠️ / ❌ **¿Certificado SSL válido y vigente?**  
- ✅ / ❌ **¿CVEs asociados a tecnologías detectadas?**

Este resumen es útil para auditorías rápidas o escaneos iniciales de exposición.

---

### ✨ Modo con Gemini AI (`gemini: true` y éxito)

Se genera un **informe profesional** en Markdown, con análisis contextual hecho por IA, incluyendo:

1. 📌 **Resumen Ejecutivo**  
2. 🌐 **Información General del Objetivo**  
3. 🔐 **Análisis de Certificado SSL/TLS**  
4. 🧩 **Encabezados HTTP/S: Seguridad y Proxy/CDN**  
5. ⚠️ **Vulnerabilidades y Riesgos Detectados**  
6. 🛠️ **Recomendaciones y Próximos Pasos**

Ideal para presentaciones técnicas, toma de decisiones y reportes a stakeholders.

---

## 📦 Artefactos Generados

Al final de cada ejecución, se sube un archivo ZIP con todos los outputs relevantes:

| Archivo                         | Descripción                                         |
|----------------------------------|-----------------------------------------------------|
| `httpx_output.json`              | Resultado del escaneo HTTPX                        |
| `whatweb_output.txt`            | Tecnologías detectadas por WhatWeb                 |
| `wafw00f_output.txt`            | Presencia de WAFs                                  |
| `nmap_output.txt`               | Estado de puertos 80 y 443                         |
| `headers_output.txt`            | Headers HTTP/S del objetivo                        |
| `cert_output.txt`               | Certificado SSL completo                           |
| `cve_resultados.txt`            | CVEs asociados a tecnologías detectadas            |
| `gateinspector_raw_logs.txt`    | Consolidado de logs de todas las herramientas      |
| `gemini_report.md` *(opcional)* | Informe detallado generado por Gemini AI           |

> 📥 Puedes descargar estos artefactos desde la página del workflow, para análisis offline o reportes.

---

## 🔑 Requisitos para usar Gemini AI

Si deseas habilitar el modo Gemini, asegúrate de:

- Crear un secreto en GitHub llamado **`GEMINI_API_KEY`**
- Obtener tu API Key desde **[Google AI Studio](https://makersuite.google.com/)**

---

## 🎯 Casos de uso

- 🔐 Auditoría pasiva de la seguridad perimetral
- 🕵️‍♂️ Reconocimiento de tecnologías y vectores expuestos
- 📈 Reportes profesionales para presentación de hallazgos
- 🤖 Análisis contextual y recomendaciones impulsadas por IA

---

## 🤝 Créditos

Este workflow fue diseñado con enfoque en análisis **pasivo**, seguro y automatizado para mejorar la visibilidad de borda en entornos productivos o de auditoría.

---
