# Aula 07 - Frameworks CSS

## Resumo da Aula

Esta aula aborda Frameworks CSS, utilitarios e metodologias de estilizacao moderna.

### Conteudo Programatico

- Introducao a Frameworks CSS
- Metodologias CSS (BEM, SMACSS, OOCSS)
- Frameworks utilitarios (Tailwind CSS)
- Frameworks de componentes (Bootstrap, Bulma)
- CSS-in-JS e solucoes modernas
- Boas praticas de organizacao de estilos

### O que sao Frameworks CSS

Frameworks CSS sao bibliotecas de estilos pre-definidos que aceleram o desenvolvimento de interfaces, fornecendo componentes prontos, sistemas de grid, tipografia e utilitarios padronizados.

### Metodologias CSS

#### BEM (Block Element Modifier)
- **Bloco**: Componente independente (`.card`)
- **Elemento**: Parte do bloco (`.card__title`)
- **Modificador**: Variacao (`.card--featured`)

#### SMACSS
Categoriza estilos em: Base, Layout, Modulo, Estado, Tema

#### OOCSS
Separa estrutura da aparencia, promove reutilizacao

### Frameworks Utilitarios

#### Tailwind CSS
- Classes utilitarias de baixo nivel
- Design system configuravel
- JIT compiler para builds otimizados
- `npm install -D tailwindcss`

```html
<button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">
  Botao
</button>
```

#### Vantagens
- Desenvolvimento rapido
- Consistencia visual
- Bundle otimizado (purge unused)
- Responsivo nativo

### Frameworks de Componentes

#### Bootstrap 5
- Componentes prontos (navbar, modal, carousel)
- Sistema de grid flexbox
- Utilitarios de espacamento/tipografia
- `npm install bootstrap`

#### Bulma
- Baseado em Flexbox
- Sem JavaScript obrigatorio
- Sintaxe limpa e semantica
- `npm install bulma`

### CSS-in-JS e Solucoes Modernas

#### Styled Components
```js
const Botao = styled.button`
  background: ${props => props.primary ? 'blue' : 'gray'};
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 4px;
`;
```

#### CSS Modules
- Escopo local automatico
- `Componente.module.css`
- Import como objeto

#### Outras
- Emotion, Stitches, Linaria
- Zero-runtime options

### Boas Praticas

1. **Mobile-first** - Comece pelo menor breakpoint
2. **Variaveis CSS** - Cores, espacamentos, breakpoints
3. **Nomenclatura consistente** - BEM ou similar
4. **Evite !important** - Use especificidade correta
5. **Organize por funcionalidade** - Nao por tipo de arquivo
6. **Documente design tokens** - Cores, fontes, espacamentos
7. **Linting** - Stylelint no pipeline

### Estrutura Recomendada

```
src/
├── styles/
│   ├── variables.css      # Custom properties
│   ├── reset.css          # Normalize/reset
│   ├── globals.css        # Estilos globais
│   ├── utilities.css      # Classes utilitarias proprias
│   └── components/        # Estilos por componente
├── components/
│   └── Button/
│       ├── Button.jsx
│       └── Button.module.css
```

### Comparacao Rapida

| Aspecto | Tailwind | Bootstrap | Bulma | CSS Modules |
|---------|----------|-----------|-------|-------------|
| Estilo | Utilitario | Componentes | Componentes | Escopo local |
| Curva | Media | Baixa | Baixa | Baixa |
| Bundle | Otimizado | Maior | Medio | Otimizado |
| JS | Opcional | Opcional | Nao | N/A |
| Customizacao | Alta (config) | Media (SASS) | Media (SASS) | Total |

### Referencias

- Tailwind CSS Docs: https://tailwindcss.com/docs
- Bootstrap Docs: https://getbootstrap.com/docs
- Bulma Docs: https://bulma.io/documentation
- BEM Methodology: https://getbem.com
- CSS Modules: https://github.com/css-modules/css-modules