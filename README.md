# link-shortt
API de encurtador de links com analytics de acessos — registra cliques, IP e user-agent de cada redirecionamento. Node.js, Express e PostgreSQL, com testes automatizados.

# Encurtador de Links com Analytics

API full stack para encurtar URLs e acompanhar estatísticas de acesso.

## Stack
- **Front-end**: HTML, CSS, JavaScript puro
- **Back-end**: Node.js + Express
- **Banco de dados**: PostgreSQL

## Funcionalidades
- Encurtamento de URL com código único gerado via `crypto`
- Redirecionamento com registro de IP, user-agent e data/hora
- Expiração opcional de links
- Página de estatísticas com total de cliques e acessos recentes
- Rate limiting nas rotas de API

## Como rodar

```bash
npm install
psql -U postgres -c "CREATE DATABASE link_shortener_db;"
psql -U postgres -d link_shortener_db -f db/schema.sql
cp .env.example .env   # edite com suas credenciais
npm start
```

Acesse `http://localhost:3000`.

## Testes

```bash
npm test
```

Os testes usam um mock do banco (não precisa de PostgreSQL rodando).

## Endpoints

| Método | Rota                       | Descrição                    |
|--------|----------------------------|-------------------------------|
| POST   | `/api/links`               | Cria um link curto            |
| GET    | `/:codigo`                 | Redireciona e registra acesso |
| GET    | `/api/links/:codigo/stats` | Retorna estatísticas do link  |

## Estrutura
```
link-shortener/
├── app.js
├── server.js
├── config/db.js
├── db/schema.sql
├── routes/links.js
├── utils/gerarCodigo.js
├── tests/
└── public/
```

## Próximos passos
- QR code automático por link
- Autenticação de usuário (dono do link)
- Gráfico de acessos por dia no front-end