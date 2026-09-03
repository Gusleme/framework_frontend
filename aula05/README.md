# Aula 05 - Criando APIs para o Front-end

## Resumo da Aula

Esta aula ensina a criar APIs REST para o Front-end utilizando Express.js, abordando servidores backend, endpoints, métodos HTTP e integração com aplicações web.

### 📋 Conteúdo Programático

- API (Application Programming Interface)
- Protocolo HTTP
- EndPoint
- JSON (JavaScript Object Notation)
- Servidor Backend e Web Service
- Criando uma API REST com Express
- Atividade prática

### 🔧 Métodos HTTP Principais

| Método | Finalidade | Características |
|--------|-----------|-----------------|
| GET | Recuperar informações do servidor | Seguro, idempotente |
| POST | Criar novos recursos no servidor | Não idempotente |
| PUT | Substituir completamente um recurso | Idempotente |
| PATCH | Atualizar parcialmente um recurso | Atualização parcial |
| DELETE | Remover um recurso específico | Idempotente |

### 📍 EndPoint

URL específica que fornece acesso a um recurso ou funcionalidade em uma API. Representa o ponto de comunicação entre o cliente e o servidor.

**Exemplo**: `https://github.com/awesomeapibrasil/awesomeapi-cep`
- GET: Lista todos os usuários
- POST: Adiciona um novo usuário

### 📄 JSON (JavaScript Object Notation)

Formato leve de troca de dados que é fácil para humanos ler e escrever e fácil para máquinas parsear e gerar. Baseado em:
- Coleções de pares nome/valor (objetos)
- Listas ordenadas de valores (arrays)

### 🖥️ Servidor Backend e Web Service

**Servidor Backend**: Sistema que processa requisições, gerencia dados e fornece respostas para clientes (apps, navegadores).

**Funções principais**:
- Armazenar/recuperar dados (banco de dados)
- Executar regras de negócio
- Fornecer APIs para comunicação

**Web Service**: Serviço acessível via web que permite comunicação entre sistemas usando HTTP/HTTPS, permitindo que sistemas heterogêneos se comuniquem de forma padronizada.

### 🚀 Criando uma API REST com Express

**Passo a passo**:

1. **Inicializando o projeto**
   - Crie uma nova pasta e abra no VS Code

2. **Instalando dependências**
   ```bash
   npm install express cors
   ```

3. **Criando o arquivo `api.js`**
   - Seguir exemplo da aula com as rotas da API

4. **Executando o servidor**
   ```bash
   node api.js
   ```

### 🛠️ Express.js

Framework minimalista e flexível para Node.js que facilita a criação de servidores web e APIs. É muito popular no ecossistema JavaScript.

### 🔒 CORS

Mecanismo de segurança que controla acesso entre domínios diferentes no navegador. Essencial para permitir que o Front-end consuma APIs de diferentes origens.

### 💡 Conceitos Importantes

- APIs são interfaces de comunicação entre sistemas
- REST define padrões para criação de APIs usando HTTP
- JSON é o formato padrão para troca de dados
- Express.js simplifica a criação de servidores Node.js
- CORS é necessário para comunicação entre diferentes domínios
