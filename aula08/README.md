# Aula 08 - Projeto React

## Resumo da Aula

Esta aula aborda o desenvolvimento de interfaces com React, incluindo JSX, componentes, props, Virtual DOM, listas, chaves e renderização condicional.

### Conteúdo Programático

- Revisão de JavaScript
- JSX: sintaxe e expressões JavaScript
- Componentes: criação, composição e reutilização
- Props: passagem de dados entre componentes
- DOM e Virtual DOM: renderização e reconciliação
- Listas e Keys: renderização de coleções de dados
- Renderização condicional: controle de exibição da interface
- Atividade prática

### Revisão de JavaScript

A aula inicia com uma revisão dos conceitos fundamentais do JavaScript:

- **Inserção de JavaScript**: tag `<script>` no corpo do HTML, arquivos externos via atributo `src`, e atributos de eventos como `onclick` e `onblur`.
- **Variáveis**: `var` (escopo de função), `let` (escopo de bloco) e `const` (escopo de bloco, valor constante). Nomes são case sensitive.
- **Tipos de dados**: String, Number, Boolean, Object, Array, Symbol, Undefined, BigInt, Null. O operador `typeof` verifica o tipo de um valor.
- **Operadores**: aritméticos (+, -, *, /, %, **, ++, --), de comparação (==, ===, !=, !==, >, <, >=, <=) e lógicos (&&, ||, !). Operadores de atribuição (=, +=, -=, *=, /=, %=).
- **Condicionais**: `if`, `else if`, `else` e operador ternário.
- **Estruturas de repetição**: `for`, `while`, `do...while`, `break` e `continue`.
- **Funções**: declaração tradicional `function nome() {}` e arrow functions `const nome = () => {}`.
- **Arrays**: armazenamento de múltiplos valores, acesso por índice, métodos como `forEach()` e `filter()`.
- **Objetos**: propriedades e métodos, palavra-chave `this`.
- **DOM**: seleção (`getElementById`, `querySelector`, `querySelectorAll`), alteração (`textContent`, `value`, `classList`), criação (`createElement`) e adição (`appendChild`) de elementos.
- **Exemplos práticos**: dark mode, botão voltar ao topo, efeito de digitação (typewriter), pop-up/modal.

### JSX

- Extensão de sintaxe para JavaScript.
- Permite escrever estruturas semelhantes a HTML dentro do JavaScript.
- Utilizado para descrever interfaces de componentes React.
- Combina a estrutura da interface com a lógica que produz seu conteúdo.
- Diferenças do HTML: `className` em vez de `class`, `htmlFor` em vez de `for`, elementos sem conteúdo devem ser fechados (`<img />`), componentes devem retornar um elemento raiz ou Fragment, valores JavaScript entre chaves `{}`.
- Expressões JavaScript são inseridas entre chaves `{}`.

### Componentes

- Unidades independentes e reutilizáveis da interface.
- Normalmente funções JavaScript que retornam elementos React.
- Geralmente utilizam JSX para descrever a estrutura visual.
- Permitem dividir uma aplicação em partes menores e organizadas.
- Deve iniciar com letra maiúscula, usar `return` e ser chamado com `<NomeDoComponente />`.
- Reutilização evita repetir estruturas semelhantes e mantém consistência visual.

### Props

- Abreviação de properties (propriedades).
- São dados recebidos por um componente React.
- Permitem enviar informações de um componente pai para um filho.
- Permitem reutilizar componentes com conteúdos diferentes.
- Tipos de valores: strings, números, booleanos, arrays, objetos, funções e elementos React.
- Fluxo de dados: pai para filho (fluxo explícito e fácil de compreender).

### DOM e Virtual DOM

- **DOM**: representação estruturada do documento HTML disponibilizada pelo navegador. Permite consultar e modificar elementos.
- **Virtual DOM**: representação da interface em memória utilizada pelo React. O desenvolvedor descreve o resultado esperado e o React coordena a atualização.
- **Diferenças**: DOM representa a estrutura no navegador e é consultado/modificado por JavaScript; Virtual DOM é um modelo conceitual para compreender as descrições da interface usadas pelo React.
- **Atualização da interface**: mudança → renderização → reconciliação → atualização.
- **Reconciliação**: processo pelo qual o React determina as mudanças necessárias entre descrições sucessivas da interface, considerando tipo do elemento, posição na árvore e propriedades `key` para identificar elementos entre irmãos.

### Listas e Keys

- Método `map()` transforma cada item de um array em um elemento da interface.
- `key` é uma propriedade especial utilizada pelo React para identificar elementos entre irmãos em uma lista.
- Ajuda o React a reconhecer quais itens foram mantidos, adicionados, removidos ou reordenados.
- Deve ser informada ao renderizar listas de elementos.
- Normalmente utiliza-se um identificador associado a cada item dos dados.
- `filter()` seleciona itens que atendem a uma condição; `map()` transforma os itens em elementos JSX.
- Preferir produzir novos arrays em vez de modificar diretamente o array existente quando a lista está em estado.

### Renderização Condicional

- Permite mostrar, ocultar ou alterar partes da interface conforme uma condição.
- Utiliza expressões e operadores JavaScript dentro do JSX.
- Adapta a interface aos dados e ao estado da aplicação.
- `if` e `return` são indicados quando cada condição exige uma resposta ou interface diferente.
- Operador ternário (`condição ? valorSeVerdadeiro : valorSeFalso`) é útil para alternar entre carregamento e resultado.
- Listas podem apresentar resultados ou mensagem quando estiverem vazias.
- Interfaces podem representar estados de carregamento, erro e sucesso.

### Atividade Prática

Desenvolver uma aplicação React que utilize todos os conceitos estudados nesta aula, incluindo JSX, componentes, props, Virtual DOM, listas e renderização condicional.

- Criar um repositório público no GitHub.
- Criar um README contendo: descrição, funcionalidades e conceitos utilizados.

### Referências

1. SOUZA, Natan. Bootstrap 4: conheça a biblioteca front-end mais utilizada no mundo. São Paulo: Casa do Código, 2018.
2. MACHADO, Kheronn Khennedy. Angular 11 e Firebase: construindo uma aplicação integrada com a plataforma do Google. São Paulo: Casa do Código, 2021.
3. EIS, Diego. Guia Front-end: o caminho das pedras para ser um dev front-end. São Paulo: Casa do Código, 2015.
4. GONÇALVES, Edson. Desenvolvendo aplicações Web com JSP, Servlets, JavaServer Faces, Hibernate, EJB 3 Persistence e Ajax. Rio de Janeiro: Ciência Moderna, 2007.
5. HARTCOPP, Patrícia Ferreira. Métrica Web. São Paulo: Contentus, 2020.
6. NIEDERAUER, Juliano. Desenvolvendo Websites com PHP: aprenda a criar Websites dinâmicos e interativos com PHP e banco de dados. 3. ed. São Paulo: Novatec, 2017.
7. PREECE, J.; ROGERS, Y.; SHARP, H. Design de Interação: além da interação Homem-Computador. 3. ed. Porto Alegre: Bookman, 2013.
8. SOUSA, Roque Fernando Marcos. Canvas HTML 5: composição gráfica e interatividade na Web. Rio de Janeiro: Brasport, 2014.

### Links Complementares

- Conceitos: https://github.com/deivisontakatu/aula-react
- Exemplo: https://github.com/deivisontakatu/projeto-react
- Aplicação: https://projeto-react-five-swart.vercel.app/
- Atividade de Revisão: https://wayground.com/
- Material: https://github.com/deivisontakatu/aula-javascript

### Professora

Prof. Me. Deivison S. Takatu
deivison.takatu@edu.senai.br