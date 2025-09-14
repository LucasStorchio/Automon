# Plataforma SaaS de Automação para YouTube

Uma plataforma completa de Software como Serviço (SaaS) para geração automatizada de conteúdo de vídeo para o YouTube, construída com arquitetura de microsserviços.

## 🚀 Características Principais

- **Geração Automatizada de Vídeos**: Pipeline completo de criação de conteúdo
- **Integração com YouTube**: Upload automático e análise de performance
- **Sistema de Assinaturas**: Múltiplos planos com Stripe
- **Arquitetura Escalável**: Microsserviços com Docker
- **Interface Moderna**: Dashboard React com TypeScript
- **Processamento Assíncrono**: Filas de tarefas com Celery

## 🛠️ Stack Tecnológica

### Backend
- **Python 3.11** com **FastAPI**
- **PostgreSQL** para persistência
- **Redis** para cache e sessões
- **RabbitMQ** como message broker
- **Celery** para processamento assíncrono

### Frontend
- **React 18** com **TypeScript**
- **Material-UI (MUI)** para componentes
- **Recharts** para visualizações
- **Vite** como bundler

### Infraestrutura
- **Docker** e **Docker Compose**
- **Nginx** como proxy reverso
- **Flower** para monitoramento de tarefas

### Integrações
- **YouTube Data API v3**
- **YouTube Analytics API**
- **ElevenLabs** para Text-to-Speech
- **OpenAI GPT** para geração de roteiros
- **Stripe** para pagamentos
- **MoviePy** para edição de vídeo

## 📁 Estrutura do Projeto

```
youtube-platform/
├── backend/
│   ├── api_gateway/          # API Gateway principal
│   ├── user_service/         # Gerenciamento de usuários
│   ├── content_service/      # Geração de conteúdo
│   ├── youtube_service/      # Integração YouTube
│   └── payment_service/      # Sistema de pagamentos
├── frontend/                 # Aplicação React
├── nginx/                    # Configuração Nginx
├── database/                 # Scripts SQL
├── shared/                   # Código compartilhado
├── media/                    # Arquivos de mídia
├── docker-compose.yml        # Orquestração de serviços
└── .env.example             # Variáveis de ambiente
```

## 🚀 Início Rápido

### Pré-requisitos
- Docker e Docker Compose
- Node.js 18+ (para desenvolvimento frontend)
- Python 3.11+ (para desenvolvimento backend)

### Configuração

1. **Clone o repositório**
```bash
git clone <repository-url>
cd youtube-platform
```

2. **Configure as variáveis de ambiente**
```bash
cp .env.example .env
# Edite o arquivo .env com suas chaves de API
```

3. **Inicie os serviços**
```bash
docker-compose up -d
```

4. **Execute as migrações do banco**
```bash
docker-compose exec api_gateway python -m alembic upgrade head
```

5. **Acesse a aplicação**
- Frontend: http://localhost
- API Docs: http://localhost/api/docs
- RabbitMQ Management: http://localhost:15672
- Flower (Celery): http://localhost:5555

## 🔧 Desenvolvimento

### Backend
Cada microsserviço pode ser desenvolvido independentemente:

```bash
cd backend/api_gateway
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
```

### Frontend
```bash
cd frontend
npm install
npm run dev
```

### Executar Testes
```bash
# Backend
docker-compose exec api_gateway pytest

# Frontend
cd frontend && npm test
```

## 📊 Monitoramento

- **Flower**: Monitoramento de tarefas Celery em tempo real
- **Logs**: `docker-compose logs -f [service_name]`
- **Health Checks**: Todos os serviços incluem health checks

## 🔐 Segurança

- Autenticação JWT com refresh tokens
- Senhas hasheadas com bcrypt
- Tokens OAuth criptografados em repouso
- Validação de webhooks do Stripe
- Variáveis de ambiente para secrets

## 📈 Escalabilidade

- Arquitetura de microsserviços
- Workers Celery escaláveis horizontalmente
- Cache Redis para performance
- Filas assíncronas para tarefas pesadas

## 🚀 Deploy em Produção

1. Configure um domínio e SSL
2. Atualize as variáveis de ambiente
3. Use um banco PostgreSQL gerenciado
4. Configure backup automático
5. Implemente monitoramento com Prometheus/Grafana

## 📝 Licença

Este projeto está licenciado sob a MIT License.

## 🤝 Contribuição

1. Fork o projeto
2. Crie uma branch para sua feature
3. Commit suas mudanças
4. Push para a branch
5. Abra um Pull Request

## 📞 Suporte

Para suporte técnico, abra uma issue no repositório ou entre em contato através do email de suporte.