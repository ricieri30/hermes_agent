# 🤖 Hermes Agent — Setup Docker

Deploy pronto para produção do [Hermes Agent](https://github.com/nousresearch/hermes-agent) via Docker/Docker Compose.

## 🚀 Deploy Rápido (VPS / Servidor Linux)

```bash
# 1. Clone este repositório
git clone https://github.com/SEU_USUARIO/hermes-agent .
cd hermes-agent

# 2. Configure suas chaves de API
cp .env.example .env
nano .env   # Edite com suas chaves

# 3. Suba o container
docker compose up -d

# 4. Veja os logs
docker compose logs -f
```

## ⚙️ Configuração

Edite o arquivo `.env` com suas credenciais:

| Variável | Descrição | Obrigatório |
|----------|-----------|-------------|
| `OPENROUTER_API_KEY` | Acesso a 200+ modelos | ✅ Uma das chaves |
| `NOUS_API_KEY` | Portal Nous Research | ✅ Uma das chaves |
| `GROQ_API_KEY` | Modelos rápidos gratuitos | ✅ Uma das chaves |
| `OPENAI_API_KEY` | Modelos OpenAI | Opcional |
| `TELEGRAM_TOKEN` | Bot Telegram | Para gateway |
| `HERMES_MODEL` | Modelo padrão | Sim |

## 📱 Modos de Uso

### Gateway (Telegram/WhatsApp/Discord) — Modo Servidor
```bash
docker compose up -d
# Hermes roda em background e responde mensagens automaticamente
```

### CLI Interativo
```bash
docker compose run --rm hermes
# Abre terminal interativo com o agente
```

### Setup inicial (primeiro uso)
```bash
docker compose run --rm hermes setup
# Wizard de configuração guiado
```

### Escolher modelo
```bash
docker compose run --rm hermes model
```

## 📂 Estrutura do Projeto

```
hermes-agent/
├── docker-compose.yml   # Configuração Docker principal
├── .env.example         # Template de variáveis (copie para .env)
├── .env                 # Suas chaves (NÃO suba para o GitHub!)
├── .gitignore
└── README.md
```

> **Nota:** O código fonte do Hermes Agent é baixado automaticamente via Docker build da imagem oficial do NousResearch. Este repositório contém apenas a configuração de deploy.

## 🛠️ Comandos Úteis

```bash
# Parar
docker compose down

# Reiniciar
docker compose restart

# Atualizar para versão mais recente
docker compose pull && docker compose up -d

# Ver logs em tempo real
docker compose logs -f hermes

# Acessar o container
docker compose exec hermes bash

# Backup dos dados (memórias, skills, etc.)
docker run --rm -v hermes_agent_hermes_data:/data -v $(pwd):/backup \
  alpine tar czf /backup/hermes_backup_$(date +%Y%m%d).tar.gz /data
```

## 🔗 Links Úteis

- [Repositório Oficial](https://github.com/nousresearch/hermes-agent)
- [Documentação Completa](https://hermes-agent.nousresearch.com/docs/)
- [OpenRouter (chaves API)](https://openrouter.ai)
- [Nous Portal](https://portal.nousresearch.com)
