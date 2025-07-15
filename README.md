# 🔍 Inspeccion Gateway

Este workflow executa uma **análise passiva de segurança** sobre um domínio ou IP, com foco na detecção de **gateways de segurança (WAF, CDN, API Gateway, Ingress, etc.)**, exposição tecnológica e certificado SSL. Opcionalmente, pode gerar um **relatório detalhado com IA Gemini**.

---

## 🚀 Como usar

1. Vá até a aba **Actions** do seu repositório.
2. Selecione o workflow **Inspeccion Gateway**.
3. Clique em **Run workflow** e preencha os campos:

- `dominio`: domínio ou IP (ex: `juice-shop.herokuapp.com`)
- `gemini`: `true` para ativar relatório com IA Gemini, `false` para análise padrão.

---

## 🔧 O que é analisado

- Tecnologias expostas (HTTPX, WhatWeb)
- Presença de WAF ou gateways (Wafw00f, headers)
- Certificado SSL/TLS (validação e validade)
- Portas abertas (80 e 443)
- Vulnerabilidades conhecidas (CVEs via CIRCL)

---

## 🧠 Modos de saída

### 🔹 Modo padrão (`gemini: false`)
Você verá um **checklist de segurança** com:

- Presença de gateway
- Passagem por proxy/CDN
- Tecnologias detectadas
- Certificado válido ou expirado
- CVEs relevantes

### 🔸 Modo com Gemini (`gemini: true`)
Gera um **relatório técnico completo** em Markdown com:

- Checklist automatizado com emojis
- Resumo executivo
- Detecção tecnológica
- Análise de SSL, headers e CVEs
- Recomendação de próximos passos

> O relatório será salvo como `gemini_report.md` nos artefatos do workflow.

---

## 📦 Artefatos gerados

Após a execução, será criado um pacote com os arquivos:

- `httpx_output.json`, `whatweb_output.txt`, `nmap_output.txt`, etc.
- `cert_output.txt` e `headers_output.txt`
- `cve_resultados.txt` com vulnerabilidades conhecidas
- `gateinspector_raw_logs.txt` (log consolidado)
- `gemini_report.md` (apenas se `gemini: true` e sucesso)

---

## 🔐 Requisitos

Para usar Gemini, adicione o segredo `GEMINI_API_KEY` no GitHub:

```bash
Settings → Secrets → New repository secret
```

---

## 📌 Exemplo rápido (Checklist)

```txt
✅ El alvo es un Gateway de Seguridad
✅ El tráfico pasa por un Gateway/Proxy
✅ Tecnología detectada
⚠️ Certificado próximo a expirar
⚠️ CVEs encontrados para tecnologías detectadas
```

---

## 🛡️ Indicado para

- Consultores de segurança
- Times de DevSecOps
- Avaliação de exposição perimetral
- Investigação passiva de ambientes

---

Made with ❤️ by CNetSec · Powered by Gemini AI
