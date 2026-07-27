# Icons

Ícones usados no README do perfil, organizados por categoria. Ficam versionados aqui em
vez de carregados de CDNs/favicons externos — assim não quebram quando um site troca de
favicon, sai do ar ou muda de domínio, e todos seguem o mesmo padrão visual.

```
icons/
├── languages/     9    ├── ai/            14
├── databases/     5    ├── automation/     4
├── cloud/        12    ├── data/           3
├── productivity/  4    └── setup/          2
```

## Padrão

| Regra | Valor |
| --- | --- |
| Formato | SVG onde há vetorial oficial; PNG quando só existe app icon (ver abaixo) |
| Canvas | `viewBox="0 0 128 128"` quadrado (PNG: 256×256) |
| Enquadramento | centralizado pelo *bounding box* real, maior dimensão ≤ 112/128 |
| Peso óptico | escala limitada também pela área visual (~100²), para glifos sólidos não dominarem os vazados |
| Uso no README | `width="45" height="45"` — sem distorção, já que todos são quadrados |

## Tema claro e escuro — o que funciona e o que não

**A armadilha:** `prefers-color-scheme` dentro de um SVG segue o tema do **sistema
operacional** de quem visita, não o tema do GitHub. Quando os dois divergem, o ícone
fica preso na variante errada e **some** — não é só perder contraste. `<picture>` com
`media=` tem exatamente a mesma limitação, porque lê o mesmo sinal.

Isso derrubou a primeira tentativa: ícones de cor única (glifo preto que virava branco)
ficavam invisíveis para quem lê o GitHub num tema diferente do SO.

**O que funciona:** ícone com contraste interno — duas cores dentro do próprio desenho.
Aí ele é legível sobre qualquer fundo, sem depender de tema nenhum. Por isso estes usam
o **app icon oficial** da marca, que já vem com fundo:

| Ícone | Origem |
| --- | --- |
| `ai/chatgpt.png` | ícone do app ChatGPT na App Store (OpenAI) |
| `ai/deepl.png` | ícone do app DeepL na App Store |
| `ai/langchain.png` | webclip oficial de `langchain.com` |
| `ai/ollama.png` | `ollama.com/public/apple-touch-icon.png` |

`ai/tavily` merece nota à parte. O SVG oficial (`tavily-mark-black.svg`) desenha o
quadrado e as setas como **recortes** (`fill-rule="evenodd"`), então as setas mostram o
que estiver atrás: no fundo claro viram brancas, no escuro viram escuras — e o ícone
inteiro some. A correção mantém a cor oficial `#1F1E1E` e duplica o path com
`fill-rule="nonzero"` em branco por baixo, de modo que os recortes passem a revelar
branco sólido em vez do fundo da página. No tema claro o resultado é idêntico ao
original; no escuro as setas continuam legíveis.

Cinco ícones ainda usam a media query, mas **sem risco**: todos têm duas cores próprias,
então continuam legíveis mesmo travados na variante errada — a media query só refina o
tom. São `ai/cursor`, `ai/manus`, `ai/mcp`, `languages/express` e
`productivity/obsidian` (este último já vem assim de fábrica, do favicon oficial).

## Origem

| Fonte | Licença | Ícones |
| --- | --- | --- |
| Brand kit / site oficial da marca | — | chatgpt, claude, clickup, cursor, langchain, obsidian, bitrix24, lovable, manus, mcp, express, streamlit, huggingface, firecrawl, tavily, traefik, powerbi, antigravity |
| [Devicon](https://devicon.dev/) | MIT | python, typescript, javascript, html5, css3, react, nextjs, nodejs, postgresql, redis, supabase, aws, gcp, cloudflare, docker, terraform, debian, postman, githubactions, jira, windows11 |
| [Simple Icons](https://simpleicons.org/) | CC0 1.0 | qdrant, nginx, ubuntu, coolify, hostinger, godaddy, deepseek, deepl, n8n, make, lookerstudio, mysql, ollama |
| [`langchain-ai/.github`](https://github.com/langchain-ai/.github) | — | langchain (símbolo extraído do logo horizontal oficial) |
| Composição própria | — | apple (ver abaixo) |

`setup/apple.svg` é o logotipo arco-íris da Apple (1977–1998), montado sobre o path do
Devicon com as seis faixas aplicadas via `clipPath`. A ordem — verde, amarelo, laranja,
vermelho, roxo, azul — está confirmada no relato do próprio Rob Janoff, que desenhou o
logo em 1977. Os valores hex não são spec oficial: a Apple aposentou esse logo em 1998 e
nunca publicou os códigos, então usamos os valores consistentes entre reconstruções.

## Ajustes de cor remanescentes

Dois ícones ainda usam cor ajustada, por serem marcas escuras sem variante publicada
pela própria marca. Foram clareados para manter ≥3:1 de contraste nos dois temas:

| Ícone | De | Para |
| --- | --- | --- |
| `cloud/aws` | `#252F3E` | `#7A869A` (só o texto; o *smile* segue `#F90`) |
| `databases/mysql` | `#00618A` | `#4479A1` (azul MySQL, variante clara) |


`cloud/gcp.png` é o `super_cloud_gradient.png` servido pelo gstatic, que o
`cloud.google.com` declara hoje como `apple-touch-icon`. A versão de quatro cores
chapadas é anterior e hoje só sobrevive no `og:image` social. Não há SVG público desse
gradiente, por isso o ícone é PNG (192×192 na origem, o maior disponível).

Se alguma dessas marcas passar a publicar variante de tema, dá para trocar pela oficial
e mover para a lista da seção anterior.

## Marcas registradas

Os logotipos pertencem aos respectivos donos e aparecem aqui apenas para identificar as
tecnologias utilizadas. Isso não implica qualquer vínculo ou endosso.
