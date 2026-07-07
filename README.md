# o-informante

**O Informante — Renda Real** — dashboard para visualizar proventos e renda anual de bilionários (perfil Forbes).

**GitHub:** https://github.com/Tonksinho/o-informante

---

## Estrutura

```
o-informante/
├── README.md
├── index.html           # Frontend (Tailwind + Swiper)
├── servidor.py          # API Flask (proventos e consolidado)
├── requirements.txt     # Dependências Python
├── vercel.json          # Config de deploy Vercel
└── *.webp / *.jpg       # Fotos dos perfis
```

---

## Stack

| Camada | Tecnologia |
|--------|------------|
| Frontend | HTML, Tailwind CSS, Swiper |
| Backend | Flask + Flask-CORS |
| Deploy | Vercel (frontend) + API externa/ngrok |

---

## Setup local

```powershell
git clone https://github.com/Tonksinho/o-informante.git
cd o-informante
pip install -r requirements.txt
python servidor.py
```

API local: `http://localhost:5001`

Abra `index.html` no navegador (ou sirva com um servidor estático). Atualize `API_URL` em `index.html` para apontar ao backend.

---

## Endpoints da API

| Método | Rota | Descrição |
|--------|------|-----------|
| GET | `/api/fortunas?ano=2025` | Renda anual por bilionário no ano |
| GET | `/api/consolidado/<perfil>` | Histórico consolidado (2021–2025) |

---

## Perfis disponíveis

Joesley, Wesley, Ronaldo, Fabio, Marcelo, Larry (Ellison), Amancio (Ortega)

---

## Commits — padrão sugerido

```
feat: novo perfil ou ano de proventos
fix: correcao no calculo de dividendos
docs: atualiza README
```

---

## Repositórios arquivados (legado)

Os repos `divid` e `dividendprogram` foram **arquivados** — use apenas este repositório.