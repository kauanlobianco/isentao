# isentão?

**Lula, Flávio ou isentão? Suas ideias respondem.**

Teste de afinidade eleitoral para o 2º turno da eleição presidencial de 2026. A pessoa responde a afirmações sobre propostas reais dos planos de governo de **Lula (PT)** e **Flávio Bolsonaro (PL)**, sem saber de quem é cada uma, e no fim vê com qual plano suas ideias mais combinam, tema por tema.

## O que tem

- **Duas versões:** curta (30 afirmações) e aprofundada (50 afirmações).
- **5 eixos, 10 polos:** Economia e Estado · Trabalho e Social · Segurança e Justiça · Educação e Saúde · Sociedade, Clima e Institucional.
- **Questionário sem distração:** barra de progresso, avanço automático, botão de voltar e atalhos de teclado (1 a 5 respondem, ← volta).
- **Resultado completo:** veredito ("Isentão nada." ou "Isentão confirmado."), placar geral, barras por eixo, seus destaques e o Raio-X visual de cada afirmação, com a proposta real e as fontes.
- **Arte para compartilhar:** pôster gerado no navegador nos formatos Stories (1080 × 1920) e Feed (1080 × 1350), com tema vermelho (Lula), azul (Flávio) ou dividido (no meio).

## Como rodar

Não precisa instalar nada. É um site estático (React, Tailwind CSS e Lucide carregados por CDN).

- Abra `index.html` no navegador, **ou**
- sirva a pasta com qualquer servidor estático, por exemplo `npx serve .` ou `python -m http.server`.

Também funciona direto no **GitHub Pages**: em *Settings → Pages*, escolha a branch `main` e a pasta raiz.

## Estrutura

| Arquivo | O que é |
|---|---|
| `index.html` | O app: início, questionário, resultado e arte de compartilhamento |
| `data.js` | Base de dados: eixos, as 50 afirmações, escala de respostas e fontes |

## Como o resultado é calculado

Cada resposta vai de −2 (discordo completamente) a +2 (concordo completamente). Cada afirmação tem um peso (1 ou 1,5) e uma direção (+1 para o polo Lula, −1 para o polo Flávio).

```
Afinidade com Lula no eixo = 50 + 50 × Σ(resposta × peso × direção) ÷ (2 × Σ peso)
Afinidade com Flávio no eixo = 100 − Afinidade com Lula
Resultado geral = média dos 5 eixos
```

Em cada eixo há o mesmo número de afirmações e o mesmo peso para os dois lados, e parte delas é escrita "invertida" (descreve a proposta de um candidato pelo ângulo contrário). Assim, quem responde "Neutro" em tudo, ou concorda com tudo, fica exatamente em 50%.

A ordem das perguntas é embaralhada em blocos de 5, com uma afirmação de cada eixo por bloco, alternando o lado que pontua.

## Editando as afirmações

As afirmações ficam em `data.js`, no array `QUESTIONS`. Cada uma tem eixo, camada (núcleo ou extra), direção, peso, texto, base factual e fontes. Ao editar, mantenha o mesmo número de afirmações e a mesma soma de pesos para os dois lados em cada eixo.

## Fontes

As afirmações resumem propostas dos planos de governo registrados no TSE em 2026, a partir das reportagens listadas em `data.js` (UOL, Agência Brasil, Gazeta do Povo, CNN Brasil, Exame, Congresso em Foco, Jornal Razão, entre outras).

## Aviso

Ferramenta educativa, sem vínculo com partidos ou campanhas. O resultado mede proximidade com as propostas escritas nos planos de governo e **não é uma recomendação de voto**. As respostas ficam só no navegador de quem responde.
