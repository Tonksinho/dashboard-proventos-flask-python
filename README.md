# Dashboard de proventos de bilionários com Flask e API REST — 7 perfis, histórico 2021–2025

**O Informante — Renda Real:** frontend estilo Forbes que consome API Flask e exibe renda anual e consolidado multi-ano de **7 bilionários** (JBS, Energia, Construção, Pharma, Oracle, Inditex), com deploy Vercel e backend desacoplado.

**GitHub:** https://github.com/Tonksinho/dashboard-proventos-flask-python

---

## Problema e resultado

| Antes | Depois |
|-------|--------|
| Dados de proventos espalhados em planilhas | Base consolidada `HISTORICO_PROVENTOS` na API |
| Visual estático sem filtro por ano/perfil | Vista geral (Swiper) + relatório consolidado por pessoa |
| Frontend acoplado ao cálculo | **API REST** (`/api/fortunas`, `/api/consolidado/<perfil>`) |

**Resultado:** consulta de renda anual e acumulada em **5 anos** (2021–2025) para **7 perfis**, com moedas BRL, USD e EUR conforme ativo, pronto para demo e deploy.

---

## Stack

| Ferramenta | Versão / nota |
|------------|---------------|
| Python | 3.10+ |
| Flask | latest |
| Flask-CORS | API consumida pelo frontend |
| gunicorn | produção |
| Frontend | HTML + Tailwind CSS + Swiper 11 |
| Deploy | Vercel (`vercel.json`) |

---

## Rodar em 3 comandos

```powershell
git clone https://github.com/Tonksinho/dashboard-proventos-flask-python.git
cd dashboard-proventos-flask-python && pip install -r requirements.txt
python servidor.py
```

Abra `index.html` e ajuste `API_URL` para `http://localhost:5001`.

---

## Decisões técnicas

**API Flask separada do HTML** — frontend deployável na Vercel enquanto cálculos de proventos (quantidade × VPA por ano) ficam no backend; facilita trocar ngrok/produção sem rebuild do layout.

**Dicionário `DADOS_BILIONARIOS` + histórico flat** — modelo simples e auditável para POC; cada ticker acumula proventos por ano sem banco relacional.

**CORS habilitado** — necessário para browser consumir API em domínio diferente (Vercel ↔ backend/ngrok).

**Repositórios legados arquivados** — `divid` e `dividendprogram` foram consolidados neste repo único.

---

## Endpoints

| Rota | Retorno |
|------|---------|
| `GET /api/fortunas?ano=2025` | Renda anual formatada por bilionário |
| `GET /api/consolidado/Joesley` | Histórico 2021–2025 + total acumulado |

---

## Estrutura

```
o-informante/
├── index.html      # UI + login + Swiper
├── servidor.py     # Flask API
├── requirements.txt
├── vercel.json
└── assets/         # fotos *.webp, *.jpg
```