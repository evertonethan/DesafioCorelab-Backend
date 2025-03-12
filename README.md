# CoreNotes Backend

![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Dotenv](https://img.shields.io/badge/Dotenv-ECD53F?style=for-the-badge&logo=dotenv&logoColor=black)
![CORS](https://img.shields.io/badge/CORS-FF6C37?style=for-the-badge&logo=cors&logoColor=white)

## 📋 Descrição

Backend do desafio Corelab Challenge - Uma API RESTful desenvolvida em Node.js com Express e MySQL para gerenciar uma aplicação de lista de tarefas. Esta API permite a criação, leitura, atualização e exclusão de notas, além de suportar a funcionalidade de favoritar itens e definir cores para cada nota.

## 🚀 Recursos

- **API RESTful completa** para gerenciamento de notas
- **CRUD** (Create, Read, Update, Delete) de todos os itens
- **Ordenação automática** (favoritos primeiro)
- **Suporte para cores** personalizadas
- **Persistência em MySQL** para armazenamento seguro e eficiente
- **Gerenciamento de ambiente** via dotenv

## 🛠️ Tecnologias

- **Node.js**: Ambiente de execução JavaScript server-side
- **Express**: Framework web para Node.js
- **MySQL**: Sistema de gerenciamento de banco de dados relacional
- **mysql2**: Módulo para conexão com MySQL
- **dotenv**: Carregamento de variáveis de ambiente
- **cors**: Middleware para habilitar CORS (Cross-Origin Resource Sharing)
- **body-parser**: Middleware para processar dados de requisições

## 📦 Instalação

Certifique-se de ter o Node.js (versão >=16.15.0) e NPM (>=8.5.5) instalados, além de um servidor MySQL.

1. Clone o repositório:
```bash
git clone https://github.com/evertonethan/DesafioCorelab-Backend.git
cd corelab-challenge-backend
```

2. Instale as dependências:
```bash
npm install
```

3. Configure o banco de dados:
   
   a. Crie o banco de dados MySQL:
   ```sql
   CREATE DATABASE IF NOT EXISTS todo_app CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
   ```
   
   b. Crie um arquivo `.env` na raiz do projeto com as seguintes configurações:
   ```
   DB_HOST=localhost
   DB_USER=seu_usuario
   DB_PASS=sua_senha
   DB_NAME=todo_app
   PORT=3001
   ```

4. Inicie o servidor:
```bash
npm start
```

5. A API estará disponível em:
```
http://localhost:3001
```

## 📊 Estrutura do Banco de Dados

```sql
CREATE TABLE IF NOT EXISTS notes (
  id INT AUTO_INCREMENT PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  content TEXT,
  color VARCHAR(20) DEFAULT '#FFFFFF',
  is_favorite BOOLEAN DEFAULT false,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

## 🔌 Endpoints da API

| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | `/api/notes` | Retorna todas as notas |
| POST | `/api/notes` | Cria uma nova nota |
| PUT | `/api/notes/:id` | Atualiza uma nota específica |
| DELETE | `/api/notes/:id` | Remove uma nota específica |

### Exemplos de Requisições

#### GET /api/notes
```bash
curl -X GET http://localhost:3001/api/notes
```

#### POST /api/notes
```bash
curl -X POST http://localhost:3001/api/notes \
  -H "Content-Type: application/json" \
  -d '{"title":"Nova Tarefa","content":"Descrição da tarefa","color":"#E2FFFA"}'
```

#### PUT /api/notes/:id
```bash
curl -X PUT http://localhost:3001/api/notes/1 \
  -H "Content-Type: application/json" \
  -d '{"title":"Tarefa Atualizada","content":"Nova descrição","color":"#FFE2C3","is_favorite":true}'
```

#### DELETE /api/notes/:id
```bash
curl -X DELETE http://localhost:3001/api/notes/1
```

## 📁 Estrutura do Projeto

```
backend/
  ├─ .env                  # Variáveis de ambiente (não versionado)
  ├─ package.json          # Dependências e scripts
  ├─ server.js             # Ponto de entrada da aplicação
  └─ README.md             # Documentação
```

## 🧪 Testes

Para implementar testes no projeto, recomenda-se adicionar Jest e Supertest:

```bash
npm install --save-dev jest supertest
```

E adicionar o script de teste no package.json:

```json
"scripts": {
  "test": "jest"
}
```

## 📋 Requisitos do Projeto

- Node.js: ^16.15.0
- NPM: ^8.5.5
- MySQL Server

## 🚧 Possíveis Melhorias

- Implementar autenticação de usuários
- Adicionar validação de entrada usando middleware como express-validator
- Implementar sistema de logging
- Adicionar testes automatizados
- Melhorar o tratamento de erros
- Implementar documentação automática da API com Swagger

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.

---

Desenvolvido para teste da Corelab Challenge 🚀