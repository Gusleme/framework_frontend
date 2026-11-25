# Aula 09 - Projeto React 02

## Resumo da Aula

Esta aula aborda conceitos avançados de React: estado com `useState`, formulários controlados, efeitos colaterais com `useEffect`, consumo de APIs, navegação com React Router e boas práticas de desenvolvimento.

### Conteúdo Programático

- State e useState: estado e atualização da interface
- Formulários: entrada e validação de dados
- useEffect: sincronização com sistemas externos
- Consumo de APIs: busca e exibição de dados
- React Router: páginas e navegação por URLs
- Atividade prática

### State e useState

O `state` é uma informação que o componente guarda, como um contador ou uma mensagem. Permite atualizar a interface conforme as ações do usuário. Quando o estado muda, o React renderiza novamente o componente para atualizar a tela.

**Por que uma variável comum não basta?**
Variáveis comuns guardam valores, mas não atualizam a tela automaticamente. Alterar uma variável não faz o React renderizar o componente novamente. Quando o componente é executado novamente, as variáveis locais são recriadas. O state permite guardar valores entre renderizações e atualizar a interface quando eles mudam.

**O que são Hooks no React?**
Hooks são funções especiais que permitem utilizar recursos do React em componentes funcionais. Permitem trabalhar com estado e outros recursos da aplicação. Seus nomes começam com `use`, como `useState` e `useEffect`. Devem ser utilizados no início do componente ou de outros Hooks, seguindo as regras do React.

**Conhecendo o Hook useState**
O `useState` permite guardar informações que podem mudar durante o uso do componente. Retorna dois elementos: o valor atual e a função para atualizá-lo. Recebe um valor inicial, como `0` para um contador. Deve ser importado do React:

```javascript
import { useState } from "react";
const [contador, setContador] = useState(0);
```

**Exemplo em Código:**
```javascript
import { useState } from "react";

function Contador() {
  const [contador, setContador] = useState(0);
  return (
    <section>
      <p>Valor: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>
        Incrementar
      </button>
    </section>
  );
}
```

### Formulários no React

**Componentes Controlados (Controlled Components)**
No React, os elementos de formulário HTML (como `<input>`, `<textarea>` e `<select>`) costumam manter seu próprio estado. A recomendação é transformar esses elementos em componentes controlados. O estado do React torna-se a "fonte única da verdade" (single source of truth). O valor do campo é definido pelo estado e atualizado por uma função manipuladora de eventos (como `onChange`).

**Criando Formulários com useState**
Para capturar o que o usuário digita, associamos o valor do input a um estado e usamos a propriedade `onChange`. O `onChange` monitora cada alteração e atualiza o estado com `event.target.value`.

```javascript
const [nome, setNome] = useState("");

<input
  type="text"
  value={nome}
  onChange={(e) => setNome(e.target.value)}
/>
```

**Manipulando o Envio (Submit)**
No envio de um formulário, o comportamento padrão do navegador é recarregar a página. No React, evitamos isso chamando `event.preventDefault()` no evento `onSubmit`.

```javascript
const handleSubmit = (event) => {
  event.preventDefault();
  alert(`Cadastro realizado para: ${nome}`);
};

<form onSubmit={handleSubmit}>
  {/* Campos e botão de envio */}
</form>
```

**Exemplo de Formulário Simples:**
```javascript
import { useState } from "react";

function Formulario() {
  const [nome, setNome] = useState("");
  const handleSubmit = (e) => {
    e.preventDefault();
    console.log("Nome enviado:", nome);
  };
  return (
    <form onSubmit={handleSubmit}>
      <label>Nome: </label>
      <input type="text" value={nome} onChange={(e) => setNome(e.target.value)} />
      <button type="submit">Enviar</button>
    </form>
  );
}
```

### Sincronização com Sistemas Externos (useEffect)

Alguns componentes precisam se conectar a redes externas, APIs, ou executar códigos que não dependem diretamente da renderização na tela. Esses efeitos colaterais (side effects) são gerenciados no React pelo Hook `useEffect`.

**O Hook useEffect**
O `useEffect` recebe uma função e um array de dependências (opcional).

```javascript
import { useEffect } from "react";

useEffect(() => {
  // Código que executa o efeito colateral
}, [dependencias]);
```

- Sem dependências: Executa a cada renderização.
- Array vazio `[]`: Executa apenas uma vez, após a montagem do componente.
- Com dependências `[valor]`: Executa quando um dos valores do array muda.

**useEffect - Ciclo de Vida**
- Montagem (Mount): Executado quando o componente entra na tela.
- Atualização (Update): Executado quando as dependências especificadas mudam.
- Desmontagem (Unmount): Função opcional de retorno (cleanup) para limpar recursos (como cancelar timers ou assinaturas).

**Exemplo Prático de useEffect:**
```javascript
import { useState, useEffect } from "react";

function Timer() {
  const [segundos, setSegundos] = useState(0);

  useEffect(() => {
    const intervalo = setInterval(() => {
      setSegundos((prev) => prev + 1);
    }, 1000);

    // Função de limpeza (cleanup)
    return () => clearInterval(intervalo);
  }, []); // Executa apenas uma vez (montagem)

  return <p>Tempo: {segundos}s</p>;
}
```

### Consumo de APIs no React

**Buscando Dados de APIs**
Para buscar dados, costuma-se usar a API nativa `fetch` ou bibliotecas como o `axios`. A requisição é disparada de dentro de um `useEffect` para carregar dados logo que a tela aparece. Os dados obtidos são armazenados no state para renderizar as informações atualizadas.

**Exemplo de Consumo de API (fetch):**
```javascript
import { useState, useEffect } from "react";

function ListaUsuarios() {
  const [usuarios, setUsuarios] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((data) => setUsuarios(data))
      .catch((error) => console.error("Erro ao buscar dados:", error));
  }, []);

  return (
    <ul>
      {usuarios.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

**Exemplo Prático com Estados de Loading e Erro:**
```javascript
import { useState, useEffect } from "react";

function BuscaDados() {
  const [dados, setDados] = useState([]);
  const [carregando, setCarregando] = useState(true);
  const [erro, setErro] = useState(null);

  useEffect(() => {
    fetch("https://api.exemplo.com/dados")
      .then((resp) => {
        if (!resp.ok) throw new Error("Erro na rede");
        return resp.json();
      })
      .then((data) => {
        setDados(data);
        setCarregando(false);
      })
      .catch((err) => {
        setErro(err.message);
        setCarregando(false);
      });
  }, []);

  if (carregando) return <p>Carregando...</p>;
  if (erro) return <p>Erro: {erro}</p>;

  return (
    <ul>
      {dados.map((item) => (
        <li key={item.id}>{item.nome}</li>
      ))}
    </ul>
  );
}
```

### React Router

**O que é o React Router?**
Por padrão, aplicações React são Single Page Applications (SPAs) que rodam em uma única página HTML. O React Router é a biblioteca padrão para adicionar navegação de páginas simulando URLs reais sem recarregar o navegador. Permite definir rotas diferentes para exibir componentes específicos com base no caminho da URL.

**Instalando o React Router**
Para usar o React Router em seu projeto, instale o pacote `react-router-dom` executando:

```bash
npm install react-router-dom
```

**Principais Componentes do React Router**
- `<BrowserRouter>`: Envolve toda a aplicação para habilitar o roteamento.
- `<Routes>`: Atua como um contêiner para definir todos os caminhos disponíveis.
- `<Route>`: Mapeia um caminho específico (`path`) para um componente específico (`element`).
- `<Link>`: Componente usado para navegar entre páginas sem recarregar a tela (substitui a tag `<a>`).

**Estrutura de Roteamento Básica:**
```javascript
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";
import Home from "./Home";
import Sobre from "./Sobre";

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Início</Link> | <Link to="/sobre">Sobre</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/sobre" element={<Sobre />} />
      </Routes>
    </BrowserRouter>
  );
}
```

**Rotas Dinâmicas e Parâmetros (useParams)**
É comum ter páginas dinâmicas, como detalhes de um produto específico (ex: `/produto/15`). Definimos parâmetros de rota usando dois pontos `:` no caminho. Usamos o Hook `useParams` do React Router para resgatar esses parâmetros de dentro do componente.

```javascript
// Definição da rota
<Route path="/produto/:id" element={<DetalheProduto />} />
```

**Exemplo de useParams:**
```javascript
import { useParams } from "react-router-dom";

function DetalheProduto() {
  const { id } = useParams();

  return (
    <section>
      <h2>Detalhes do Produto</h2>
      <p>Visualizando o produto com ID: {id}</p>
    </section>
  );
}
```

**Navegação Programática (useNavigate)**
Às vezes, a navegação deve acontecer automaticamente via código (após o usuário enviar um formulário ou fazer login, por exemplo). O Hook `useNavigate` retorna uma função que permite redirecionar o usuário programaticamente.

```javascript
import { useNavigate } from "react-router-dom";

function Login() {
  const navigate = useNavigate();

  const lidarComLogin = () => {
    // Autentica o usuário...
    navigate("/dashboard"); // Redireciona
  };

  return <button onClick={lidarComLogin}>Entrar</button>;
}
```

**Páginas Não Encontradas (Rota 404)**
Para tratar rotas inexistentes, podemos definir um caminho curinga `*` no final das nossas rotas. Qualquer URL que não coincida com as rotas anteriores exibirá esse componente.

```javascript
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/sobre" element={<Sobre />} />
  <Route path="*" element={<Pagina404 />} />
</Routes>
```

### Atividade Prática

**Escopo da Atividade Prática**
Criar uma aplicação React estruturada e funcional contendo:

- Página de Feed/Portfólio: Listar dados vindos de uma API pública.
- Navegação completa com React Router: Página Inicial, Detalhes e Página 404.
- Página de Contato: Formulário controlado com validações simples de campos.
- Layout Responsivo: Estilização limpa utilizando CSS Modules ou Styled Components.

**Escopo da Atividade - Detalhes da API**
Para a listagem de dados na página de Feed/Portfólio, utilize uma API REST pública e gratuita.

Sugestões de APIs para consumo:
- JSONPlaceholder (`/posts` ou `/users`): https://jsonplaceholder.typicode.com/
- GitHub API (Listar repositórios de um usuário): https://api.github.com/users/SEU-USUARIO/repos
- Rick and Morty API (Listar personagens): https://rickandmortyapi.com/api/character

**Escopo da Atividade - Requisitos do Formulário**
O formulário de contato deve ser um componente controlado com os seguintes campos:
- Nome (mínimo de 3 caracteres).
- E-mail (validar formato contendo `@` e `.com`).
- Mensagem (mínimo de 10 caracteres).
- Exibir mensagens de erro em tempo real abaixo de cada campo caso as regras não sejam atendidas.
- Desabilitar o botão de envio se houver erros de validação ativos.

**Escopo da Atividade - Gerenciamento de Rotas**
A estrutura de navegação do `react-router-dom` deve possuir os seguintes caminhos:
- `/` (Home/Feed com a listagem da API selecionada).
- `/contato` (Formulário de contato validado).
- `/detalhes/:id` (Exibição detalhada do item clicado na listagem, obtendo o parâmetro via `useParams`).
- `*` (Página de erro 404 personalizada com botão para voltar para a página inicial).

**Dicas para Desenvolvimento**
- Organize a estrutura de pastas do seu projeto:
  - `src/components/` para componentes reutilizáveis (botões, inputs).
  - `src/pages/` para os componentes principais de páginas (Home, Contato, Detalhes, 404).
  - `src/routes/` ou diretamente no `App.jsx` para a configuração de rotas.
- Use o `useEffect` com array de dependências vazio `[]` para garantir que a requisição de busca à API ocorra apenas uma vez durante o carregamento inicial da página de Feed.

**Critérios de Avaliação**
- Funcionalidade: O roteamento está funcionando sem quebras e os dados estão sendo buscados e exibidos na tela corretamente?
- Qualidade do Código: Uso correto dos Hooks (`useState`, `useEffect`, `useParams`, `useNavigate`) e boas práticas na organização dos arquivos?
- Validação: O formulário de contato impede envios inválidos e fornece feedback claro para o usuário?
- Visual/UX: Layout limpo, organizado, legível e totalmente responsivo para dispositivos móveis?

**Instruções de Entrega**
- O projeto deve ser versionado no GitHub em um repositório público ou privado (compartilhado com o professor).
- Faça o deploy da aplicação em plataformas gratuitas de hospedagem para facilitar a avaliação online:
  - Vercel (recomendado): https://vercel.com/
  - Netlify: https://www.netlify.com/
- O arquivo `README.md` do repositório deve conter instruções claras de como rodar o projeto localmente (`npm install` seguido de `npm run dev`).

### Boas Práticas no React

- **Imutabilidade**: Nunca altere o estado diretamente (ex: `estado = novoValor`). Use sempre a função correspondente (ex: `setEstado(novoValor)`).
- **Componentização**: Se um trecho de código JSX começar a ficar muito longo ou repetitivo, divida-o em componentes menores e mais fáceis de manter.
- **Chaves Únicas (Keys)**: Ao usar `.map()` para listar elementos, certifique-se de adicionar uma propriedade `key` única no elemento pai retornado (como o ID vindo do banco ou da API).

### Próximos Passos no Estudo de React

- Gerenciamento de Estado Global: Conhecer a Context API nativa do React ou bibliotecas externas como Redux e Zustand para lidar com dados que precisam ser compartilhados por muitos componentes distantes.
- Performance: Estudar Hooks de otimização como `useMemo` e `useCallback` para evitar re-renderizações desnecessárias em partes pesadas da árvore de componentes.
- Testes: Aprender a criar testes unitários e de integração utilizando Jest e React Testing Library para garantir a robustez do software.

### Referências

1. SOUZA, Natan. Bootstrap 4: conheça a biblioteca front-end mais utilizada no mundo. São Paulo: Casa do Código, 2018.
2. MACHADO, Kheronn Khennedy. Angular 11 e Firebase: construindo uma aplicação integrada com a plataforma do Google. São Paulo: Casa do Código, 2021.
3. EIS, Diego. Guia Front-end: o caminho das pedras para ser um dev front-end. São Paulo: Casa do Código, 2015.
4. GONÇALVES, Edson. Desenvolvendo aplicações Web com JSP, Servlets, JavaServer Faces, Hibernate, EJB 3 Persistence e Ajax. Rio de Janeiro: Ciência Moderna, 2007.

### Links Complementares

- Conceitos: https://github.com/deivisontakatu/aula-react
- Exemplo: https://github.com/deivisontakatu/projeto-react
- Aplicação: https://projeto-react-five-swart.vercel.app/

### Professora

Prof. Me. Deivison S. Takatu
deivison.takatu@edu.senai.br