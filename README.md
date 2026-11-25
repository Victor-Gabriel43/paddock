# Paddock — A Enciclopédia da Fórmula 1

A história da Fórmula 1 desde 1950: temporadas, corridas, pilotos, equipes, carros, circuitos, engenharia e regulamentos. Em português (padrão) e inglês (`/en`).

## Rodar

Requer Node.js 20+.

```bash
npm install
npm run dev     # http://localhost:3000
npm run build   # build de produção
npm run start   # serve o build
```

## Seções

| Rota | Conteúdo |
| --- | --- |
| `/history`, `/history/[era]` | A F1 década a década, com as corridas que marcaram cada uma |
| `/seasons`, `/seasons/[ano]`, `/seasons/[ano]/[corrida]` | Todas as temporadas de 1950 a 2026: calendário, resultados e classificação |
| `/drivers`, `/teams`, `/cars`, `/circuits` | Pilotos, equipes (com todos os carros), carros e circuitos |
| `/engineering`, `/regulations` | Engenharia e regulamentos, com arquivo da FIA, comparação e busca |
| `/race-weekend`, `/categories`, `/learn` | Como funciona um fim de semana de corrida, categorias e guias |
| `/search`, `/about` | Busca global e créditos |

URLs sem prefixo são em português. A versão em inglês fica em `/en/...`.

## Onde ficam as coisas

```
app/(site)/[lang]/   páginas (uma árvore por idioma) e site.css (design system)
app/api/search/      endpoint da busca
components/site/     componentes da interface
lib/f1/              conteúdo editorial e camada de dados
lib/i18n/            idiomas e textos da interface
data/f1/             dados das temporadas (gerados a partir da F1DB)
data/regulations/    arquivo de regulamentos da FIA
public/media/        fotos, logos e traçados
scripts/             pipelines de dados (F1DB, FIA, mídia)
proxy.ts             roteamento de idioma
```

## Dados e fotos

- **Resultados:** a fonte é a [F1DB](https://github.com/f1db/f1db) (CC BY 4.0). Os vencedores e campeões são conferidos com a API Jolpica. O JSON gerado fica no repositório, então o build não precisa de internet. Para atualizar, rode `F1DB_DIR=/caminho/da/f1db node scripts/f1db/build.mjs`.
- **Fotos:** registradas em `lib/f1/media.ts` com fonte, autor e licença. Quando não há foto verificada, a página mostra uma placa tipográfica no lugar, nunca uma foto substituta.

## Stack

Next.js 16 (App Router) + React 19 + TypeScript + Tailwind CSS 4.

## Publicar (Vercel)

Importe o repositório na Vercel. Ela detecta o Next.js sozinha e não precisa de variável de ambiente.

## Origem

O projeto nasceu dentro do repositório do LMU Race Engineer (telemetria do Le Mans Ultimate). Este branch tem só o Paddock: o app de Le Mans, o servidor e o código compartilhado foram removidos.
