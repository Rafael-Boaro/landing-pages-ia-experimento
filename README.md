# Landing Pages Geradas por IA - Experimento de Prompt Engineering

> **Um único prompt. Um endereço do Google Maps. Um site pronto para publicar.**

Este repositório documenta um experimento simples, mas revelador: até onde um **prompt bem projetado** consegue levar uma IA generativa na criação de landing pages profissionais, sem intervenção manual de design ou código.

## O experimento

A metodologia foi a seguinte, repetida **17 vezes** para negócios reais de diferentes segmentos (clínicas médicas, moda, alimentos, cosméticos etc.):

1. Busquei a ficha do negócio no **Google Maps** (nome, endereço, telefone, avaliações, fotos, horário de funcionamento, especialidades).
2. Colei essas informações **no final** de um prompt fixo, cuidadosamente arquitetado [`prompts/prompt-front.txt`](./prompts/prompt-front.txt).
3. Enviei o prompt para a IA, sem nenhuma edição manual posterior no código.
4. O resultado saiu como um único arquivo `index.html` completo, responsivo, com copywriting persuasivo e pronto para deploy.

Nenhuma das páginas abaixo foi retocada manualmente. A variação de qualidade entre elas mostra o que muda quando só o *input* (as informações do negócio) muda O prompt e o "cérebro" por trás permanecem os mesmos.

## Por que isso importa

A diferença entre uma IA generativa "genérica" e uma IA que entrega um **produto de agência** não está apenas no modelo está em como você conversa com ele. Este prompt não pede apenas "crie um site". Ele exige explicitamente:

| Categoria | O que o prompt determina |
|---|---|
| **Arquitetura** | Arquivo único, seções comentadas como módulos (`[ HEADER ]`, `[ HERO ]`, `[ FEATURES ]`), JS Vanilla com responsabilidade única |
| **Copywriting** | Estrutura PAS + AIDA - promessa no Hero, agitação do problema, solução visual, prova social realista, FAQ e CTA final |
| **UI/UX & Neurodesign** | Lei de Hick (foco em um único CTA primário), whitespace generoso, glassmorphism onde fizer sentido |
| **Performance** | Lazy loading, `defer` em scripts, animações via `transform`/`opacity` para manter 60 FPS |
| **Acessibilidade** | Hierarquia rígida de headings, atributos ARIA, navegação 100% por teclado |
| **Imagens** | Proibido espaço em branco: imagens reais do Unsplash ou placeholders `placehold.co` com dimensões exatas |
| **Manutenibilidade** | Objeto `AppConfig` centralizado no topo do script (WhatsApp, telefone, redes sociais) alimentando todos os `href` dinamicamente |

Veja o prompt completo em [`prompts/prompt-front.txt`](./prompts/prompt-front.txt).

Como bônus, o repositório também inclui um segundo prompt [`prompts/prompt-geo-seo.txt`](./prompts/prompt-geo-seo.txt) usado para gerar a infraestrutura de dados de cada site (`llms.txt`, `sitemap.xml` e Schema Markup em JSON-LD), otimizando as páginas tanto para SEO tradicional (Google) quanto para **GEO** (Generative Engine Optimization ser encontrado e recomendado por ChatGPT, Gemini, Perplexity etc.).

## Estrutura do repositório

```
.
├── README.md
├── prompts/
│   ├── prompt-front.txt        # Prompt principal: gera o front-end completo
│   └── prompt-geo-seo.txt      # Prompt bônus: gera llms.txt, sitemap.xml e Schema.org
└── examples/
    ├── index.html               # Galeria com todos os exemplos
    └── *.html                   # 17 landing pages geradas, uma por negócio
```

## Exemplos gerados

17 landing pages, cada uma a partir de uma ficha real do Google Maps. Abra qualquer `.html` diretamente no navegador são arquivos 100% autocontidos (sem build, sem dependências além de CDNs públicas).

### Saúde & Bem-estar

| Landing page | Segmento |
|---|---|
| [`gabriela-faria-odontologia.html`](./examples/gabriela-faria-odontologia.html) | Odontologia |
| [`clinderm-dermatologia.html`](./examples/clinderm-dermatologia.html) | Dermatologia |
| [`clinica-olhos-gerscovich.html`](./examples/clinica-olhos-gerscovich.html) | Oftalmologia |
| [`clinica-prognosys-ginecologia.html`](./examples/clinica-prognosys-ginecologia.html) | Ginecologia e Obstetrícia |
| [`clinsaude-cirurgia.html`](./examples/clinsaude-cirurgia.html) | Cirurgia e Cuidado Humanizado |
| [`dra-luciana-radiologista.html`](./examples/dra-luciana-radiologista.html) | Radiologia / Ultrassom |
| [`ip-geriatria.html`](./examples/ip-geriatria.html) | Geriatria e Clínica Médica |
| [`clinica-fisioterapia-pelvica.html`](./examples/clinica-fisioterapia-pelvica.html) | Fisioterapia Pélvica |
| [`clinica-sensita-psicoterapia.html`](./examples/clinica-sensita-psicoterapia.html) | Psicoterapia |
| [`elis-pires-psicologa.html`](./examples/elis-pires-psicologa.html) | Psicologia / Neuropsicologia |

### Varejo & Moda

| Landing page | Segmento |
|---|---|
| [`loja-toda-perfeita.html`](./examples/loja-toda-perfeita.html) | Moda Feminina |
| [`loja-virtue.html`](./examples/loja-virtue.html) | Moda Feminina / Modesta |
| [`dalilla-tecidos.html`](./examples/dalilla-tecidos.html) | Tecidos e Aviamentos |
| [`armazem-bebe-kids.html`](./examples/armazem-bebe-kids.html) | Roupas Infantis |
| [`afiacao-cosmeticos.html`](./examples/afiacao-cosmeticos.html) | Afiação de Utensílios / Cosméticos |

### Alimentos & Outros

| Landing page | Segmento |
|---|---|
| [`emporio-sao-jose.html`](./examples/emporio-sao-jose.html) | Produtos Gourmet e Importados |
| [`fernando-tintas.html`](./examples/fernando-tintas.html) | Loja de Tintas |

> Abra [`examples/index.html`](./examples/index.html) para navegar por todos os exemplos em uma galeria visual.

## Tecnologias e Especificação

| Camada / Pilar | Tecnologia | Finalidade |
|---|---|---|
| Modelos de Linguagem | LLMs com Ampla Janela de Contexto | Geração estruturada de código e copywriting contextual |
| Estrutura & Semântica | HTML5 Semântico, ARIA | Acessibilidade, SEO técnico e conformidade com leitores de tela |
| Estilização & UI | Tailwind CSS (via CDN) | Responsividade mobile-first, neurodesign e glassmorphism |
| Interatividade & Configuração | JavaScript Vanilla (ES6+) | Mapeamento dinâmico de `AppConfig` e microinterações leves |
| Otimização para Buscadores | Schema.org JSON-LD, GEO (`llms.txt`) | Indexação por robôs tradicionais e sistemas RAG/LLMs |


## Como reproduzir o experimento

1. Copie o conteúdo de [`prompts/prompt-front.txt`](./prompts/prompt-front.txt).
2. No final do prompt, cole as informações reais do negócio (nome, endereço, telefone, WhatsApp, especialidades/produtos, avaliações do Google, horário de funcionamento, diferenciais).
3. Envie para o seu modelo de IA generativa de preferência (recomendado: modelos com boa capacidade de código e janela de contexto ampla).
4. Salve a resposta como `index.html` e abra no navegador. Pronto para publicar em qualquer host estático (Netlify, Vercel, GitHub Pages, Cloudflare Pages).
5. *(Opcional)* Rode o segundo prompt [`prompts/prompt-geo-seo.txt`](./prompts/prompt-geo-seo.txt) passando as mesmas informações do negócio, para gerar `llms.txt`, `sitemap.xml` e o Schema Markup do site.

## Notas e limitações

- Todos os sites usam URLs de exemplo/placeholder (telefones, endereços e domínios genéricos ou fictícios) e **não foram publicados oficialmente** em nome dos negócios reais.
- As imagens vêm de bancos públicos (Unsplash) ou de `placehold.co` para uso comercial real, o ideal é substituí-las por fotos autorizadas do próprio negócio.
- O objetivo deste repositório é **demonstrativo/educacional**: mostrar o poder de um prompt bem escrito, não servir como produto final para os negócios citados.

## Licença

Os prompts e o código deste repositório estão sob licença [MIT](./LICENSE) sinta-se à vontade para usar, adaptar e melhorar.
