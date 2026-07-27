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
| Formato | SVG (vetorial) — exceto `ai/antigravity.png` e `cloud/gcp.png`, sem SVG público |
| Canvas | `viewBox="0 0 128 128"` quadrado (PNG: 256×256) |
| Enquadramento | centralizado pelo *bounding box* real, maior dimensão ≤ 112/128 |
| Peso óptico | escala limitada também pela área visual (~100²), para glifos sólidos não dominarem os vazados |
| Uso no README | `width="45" height="45"` — sem distorção, já que todos são quadrados |

## Ícones que se adaptam ao tema do GitHub

Dez ícones trazem a media query **dentro do próprio SVG**, então mudam de cor conforme
o tema de quem está lendo:

```css
:root { --c0: #000 }
@media (prefers-color-scheme: dark) { :root { --c0: #fff } }
```

`ai/chatgpt` · `ai/cursor` · `ai/langchain` · `ai/manus` · `ai/mcp` · `ai/ollama` ·
`ai/tavily` · `ai/deepl` · `languages/express` · `productivity/obsidian`

Não é invenção nossa: **o favicon oficial do ChatGPT e o do Obsidian já vêm assim**. Nos
demais, a técnica foi aplicada usando as cores que a própria marca publica para cada
fundo — o Cursor, por exemplo, distribui `favicon.svg` e `favicon-light.svg` separados,
e a LangChain mantém `logo-dark.svg` (`#030710`) e `logo-light.svg` (`#7FC8FF`) no
repositório [`langchain-ai/.github`](https://github.com/langchain-ai/.github).

Atenção ao caçar o logo da LangChain: o `logo.svg` ainda servido em `langchain.com` é o
**símbolo antigo** (elo de corrente). O atual, pós-rebrand, é a hélice de quatro pétalas
— confirmável no header do site e no avatar do org no GitHub. O ícone daqui foi extraído
do logo horizontal oficial, isolando os 4 paths do símbolo (medidos por `getBBox`), que
ocupam exatamente `0 0 488 488`.

Detalhe de implementação: os atributos herdados (`fill`, `stroke`) ficam na tag `<svg>`
raiz, não no `<g>` de transformação. Se descessem para o `<g>`, ficariam mais próximos
dos paths do que a regra `:root` do `<style>`, invertendo a cascata e apagando o ícone.

**Limitação:** `prefers-color-scheme` segue o tema do sistema operacional de quem
visita, não a preferência salva no GitHub. Quem usa "sync with system" (o padrão) vê
sempre a variante certa.

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
