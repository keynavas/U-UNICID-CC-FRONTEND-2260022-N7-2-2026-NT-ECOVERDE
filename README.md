# EcoVerde & Itaipu Sustentável

Portal web educativo, responsivo e acessível que integra **sustentabilidade**, **energia limpa** (com estudo de caso da Usina Binacional de Itaipu) e **inclusão social** (causa Setembro Verde e acessibilidade digital).

| Item | Informação |
|---|---|
| Equipe | Promptdão |
| Integrantes | Alexandre Almeida de Jesus Nogueira, Khevyn Lopes dos Santos, Luis Plinio Cornélio Mota, Marcos Paulo Cornélio Mota, Yuri Navas Moreira |
| Disciplina | Front-End para Web – Prof. Paulo Sérgio Fratta |
| Instituição | UNICID – Universidade Cidade de São Paulo |
| Data do escopo | 21/09/2026 |

## Objetivo

Desenvolver um portal web responsivo, semântico e totalmente acessível (HTML5/CSS3) para promover a educação ambiental – reciclagem e energias renováveis como a de Itaipu – e apoiar a causa do Setembro Verde com uma página de doação.

## Tecnologias

- **HTML5 semântico** (`header`, `nav`, `main`, `section`, `article`, `aside`, `footer`).
- **CSS3 puro** com variáveis (design tokens), Grid e Flexbox – um único arquivo, `css/style.css`.
- **JavaScript nativo** apenas onde necessário (`js/script.js`, ~15 KB sem minificação, sem bibliotecas).
- Sem frameworks, sem fontes externas e sem dependências de terceiros.

## Estrutura

```
/
├── index.html                  Início: hero, pilares, carrossel e dicas
├── sobre.html                  História, cronograma, missão, visão e valores
├── itaipu.html                 Estudo de caso sobre a Usina de Itaipu
├── doacao.html                 Setembro Verde + formulário de doação
├── acessibilidade.html         Recursos de acessibilidade do portal
├── galeria.html                Galeria de imagens com legendas e fontes
├── midia.html                  Vídeo, áudio/podcast e mapa (iframe)
├── noticias.html               Blog com cards por categoria
├── contato.html                Formulário de contato + equipe
├── orcamento_hospedagem.html   Comparativo de hospedagem verde e domínios
├── css/style.css
├── js/script.js
├── assets/
│   ├── images/   Ilustrações SVG originais + pôster do vídeo (WebP)
│   ├── icons/    Logo e ícones SVG
│   └── media/    Vídeo MP4, legendas WebVTT e áudio MP3
└── docs/
    ├── README.md
    ├── diario-de-bordo.md
    ├── orcamento-hospedagem.md
    └── evidencias-testes.md
```

## Como executar

O site é estático: basta abrir o `index.html` no navegador.

Recomenda-se, porém, usar um servidor local – alguns navegadores bloqueiam as **legendas do vídeo** (arquivo `.vtt`) quando a página é aberta diretamente pelo sistema de arquivos (`file://`):

```bash
# Opção 1 – Python
python -m http.server 8000

# Opção 2 – Node.js
npx serve .
```

Depois, acesse `http://localhost:8000`. No VS Code, a extensão *Live Server* também funciona.

> O mapa da Central de Mídia é carregado do OpenStreetMap e precisa de conexão com a internet.

## Recursos implementados

### Componentes globais (todas as páginas)
- Skip link “Pular para o conteúdo principal”.
- Barra de acessibilidade com teclas de atalho (padrão eMAG: 1 conteúdo, 2 menu, 3 rodapé, 4 acessibilidade), alto contraste e ajuste do tamanho do texto (preferências salvas no navegador).
- Header com menu global de 10 links, página atual indicada visualmente e com `aria-current="page"`; menu recolhível em telas menores que 1100 px (fecha com `Esc`).
- Trilha de navegação (breadcrumb) nas páginas internas.
- Footer com navegação, links de acessibilidade e informações institucionais.

### Por página
- **Início:** hero com CTAs, cards dos três pilares, carrossel acessível (botões, indicadores, setas do teclado; rotação automática desligada por padrão e oculta para quem prefere movimento reduzido).
- **Itaipu:** artigo com índice, etapas da geração hidrelétrica, cards e destaques; dados específicos marcados como “A complementar”.
- **Setembro Verde:** formulário com validação HTML5 nativa (`required`, `type="email"`, `type="tel"` + `pattern`, `type="number"` + `min`), mensagens de erro em texto associadas por `aria-describedby`, campo “Outro valor” condicional.
- **Mídia:** `<video controls poster>` com legendas WebVTT e transcrição; `<audio controls>` com transcrição; `<iframe>` com `title` descritivo e alternativa em texto.
- **Contato:** formulário validado e cards dos cinco integrantes.
- **Orçamento:** três tabelas acessíveis (`caption`, `th scope`) e roláveis em telas pequenas.

## Conteúdo pendente (não inventado)

Seguindo o escopo, nenhum dado factual ausente do briefing foi inventado. Os pontos abaixo estão marcados no site com borda tracejada e rótulo **“A complementar”** (ou `[a preencher]`) e com comentários no código:

- Dados oficiais da Usina de Itaipu (capacidade, produção, programas socioambientais) e URLs das fontes.
- Histórico oficial do Setembro Verde e destino das doações.
- Notícias reais (os cards atuais são **demonstrativos**, com data e fonte “a definir”).
- Fornecedores, planos e preços de hospedagem e domínio.
- Canais oficiais de contato da equipe.
- Vídeo e episódios oficiais do podcast (os arquivos atuais são **demonstrativos**).

## Integrações pendentes

Os formulários **não enviam dados**: sem backend, o JavaScript interrompe o envio após a validação e exibe uma confirmação de interface. Para uso real, definir o atributo `action` do formulário e remover o `preventDefault()` em `js/script.js` (função `iniciarFormulario`). **Nenhum pagamento é processado** na página de doação.

## Imagens e créditos

Todas as imagens são ilustrações vetoriais (SVG) **originais**, criadas para o projeto – leves e sem restrição de licença. Ao substituí-las por fotografias de bancos livres (Unsplash, Pexels), converter para WebP e indicar autor e fonte na legenda. Mapa: © colaboradores do OpenStreetMap.

## Paleta e contraste

| Cor | Hex | Uso |
|---|---|---|
| Verde Folha | `#2E7D32` | Sustentabilidade; botões principais (branco sobre ela: 5,1:1) |
| Azul Hidro | `#0288D1` | Itaipu/água; **apenas decorativo** (3,9:1 sobre branco). Texto usa `#01579B` (7,4:1) |
| Setembro Verde | `#7CB342` | Inclusão; recebe **texto escuro** (6,4:1). Texto verde usa `#33691E` (6,6:1) |
| Fundo Claro | `#F5F5F5` | Fundo das páginas |
| Texto Escuro | `#212121` | Texto principal (14,8:1 sobre o fundo) |
