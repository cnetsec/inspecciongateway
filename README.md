# 🔍 Inspeccion Gateway

Workflow de GitHub Actions para análisis pasivo de seguridad en dominios o IPs, con enfoque en detección de **WAFs, Gateways, Ingress, CDNs** y certificado SSL. Opcionalmente, genera un informe detallado con **IA Gemini**.

## 🚀 Uso

1. Ve a la pestaña **Actions** del repositorio.  
2. Selecciona **Inspeccion Gateway** → **Run workflow**.  
3. Rellena los campos:

- `dominio`: dominio o IP (ej: juice-shop.herokuapp.com)  
- `gemini`: `true` para generar informe con Gemini, `false` para modo estándar.

## 🧪 Qué hace

- Detecta tecnologías (HTTPX, WhatWeb)  
- Analiza headers y certificado SSL  
- Escanea puertos 80 y 443 (Nmap)  
- Detecta WAFs y proxies  
- Consulta CVEs (CIRCL)

## 📋 Salida

- ✅ Checklist resumido (modo estándar)  
- 📄 `gemini_report.md` (si Gemini está activado)  
- Archivos técnicos: `httpx_output.json`, `cert_output.txt`, `cve_resultados.txt`, etc.

## 🔐 Requisitos para Gemini

Agregar secreto `GEMINI_API_KEY` en GitHub:
``Settings → Secrets → New repository secret``

---

Made with ❤️ by CNetSec · Potenciado por Gemini AI
