# Aula 04 - Consumindo APIs no Front-end

## Resumo da Aula

Esta aula aborda o consumo de APIs no Front-end, protocolos HTTP, métodos de requisição e criação de APIs REST com Express.

### 📋 Conteúdo Programático

- API (Application Programming Interface)
- Protocolo HTTP
- EndPoint
- JSON (JavaScript Object Notation)
- Servidor Backend e Web Service
- Criando uma API REST com Express
- Atividade prática

### 🌐 O que é uma API?

Interface de Programação de Aplicações - conjunto de protocolos, rotinas e ferramentas que define como diferentes componentes de software devem interagir, permitindo que sistemas distintos se comuniquem.

### 📡 Protocolo HTTP

Modelo cliente-servidor baseado em texto:
- **Cliente**: Navegador que faz requisições
- **Servidor**: Processa requisições e retorna respostas
- **Stateless**: Cada requisição é independente

### 🔧 Métodos HTTP Principais

| Método | Finalidade | Características |
|--------|-----------|-----------------|
| GET | Recuperar informações | Seguro, idempotente |
| POST | Criar novos recursos | Não idempotente |
| PUT | Substituir recurso completamente | Idempotente |
| PATCH | Atualizar parcialmente recurso | - |
| DELETE | Remover recurso específico | Idempotente |

### 🎯 REST (Representational State Transfer)

Estilo arquitetural para sistemas distribuídos:
- Comunicação cliente-servidor sem estado
- Uso de métodos HTTP
- Recursos identificados por URIs
- Representações de dados (JSON)

### 📍 EndPoint

URL específica que fornece acesso a um recurso ou funcionalidade em uma API. Representa o ponto de comunicação entre cliente e servidor.

**Exemplo**: `https://github.com/awesomeapibrasil/awesomeapi-cep`

### 🔄 Como funciona uma requisição na prática

1. Usuário acessa página ou clica em botão
2. Navegador envia requisição HTTP (GET, POST, PUT, DELETE)
3. Servidor Express.js recebe e processa a requisição
4. Backend busca/grava dados no banco ou API externa
5. Servidor retorna resposta em JSON
6. Front-end atualiza a tela com os dados recebidos

### 🛠️ Tecnologias Envolvidas

- **Express.js**: Framework para criação de APIs REST
- **JSON**: Formato de dados padrão para comunicação
- **HTTP**: Protocolo de comunicação web

### 💡 Conceitos Importantes

- APIs permitem integração entre sistemas diferentes
- REST define boas práticas para arquitetura de APIs
- JSON é o formato mais utilizado para troca de dados
- O consumo de APIs no Front-end é feito via `fetch()` ou bibliotecas como Axios
