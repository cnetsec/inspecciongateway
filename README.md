# 🔍 Inspeccion Gateway

Workflow de GitHub Actions para análisis pasivo de seguridad en dominios o IPs, enfocado en detección de **WAFs, Gateways, Ingress, CDNs** y certificado SSL. Puede generar un informe detallado con **IA Gemini**.

> ⚠️ **Este proyecto fue creado con fines educativos. No debe ejecutarse sin autorización explícita del propietario del objetivo.**

<img width="1080" height="1104" alt="image" src="https://github.com/user-attachments/assets/86cf7485-a961-432f-a720-c120cbf1861b" />

## 🚀 Uso

1. Ve a la pestaña **Actions** del repositorio.  
2. Selecciona **Inspeccion Gateway** → **Run workflow**.  
3. Completa los campos:

- `dominio`: dominio o IP (ej: juice-shop.herokuapp.com)  
- `gemini`: `true` para generar informe con Gemini, `false` para análisis estándar.

## 🧪 Qué analiza

- Tecnologías expuestas (HTTPX, WhatWeb)  
- Cabeceras HTTP/S y certificado SSL  
- Puertos 80 y 443 (Nmap)  
- WAFs / proxies detectados  
- CVEs asociados (CIRCL)

## 📄 Resultados

- ✅ Checklist estándar (en logs)  
- 📄 `gemini_report.md` (si se activa Gemini)  
- Otros: `httpx_output.json`, `cert_output.txt`, `cve_resultados.txt`, etc.

## 🔐 Para usar Gemini

Agregar secreto `GEMINI_API_KEY` en GitHub:  
``Settings → Secrets → New repository secret``


Made with por CNetSec · Potenciado por Gemini AI
