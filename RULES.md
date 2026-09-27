# Regras da Apple Design Skill (Spec-Driven)

As regras que o agente **deve** seguir ao aplicar esta skill. Elas também estão embutidas
em `SKILL.md`; este arquivo é a referência rápida e citável.

## Processo
1. **Nunca pule para o código.** Todo pedido passa pelo pipeline
   `requirements → design → tasks → implementação → verify`.
2. **Um gate por vez.** Não avance de fase sem a aprovação explícita do usuário.
3. **"Só constrói" não pula o design.** Se o usuário tiver pressa, gere uma
   `requirements.md` + `design.md` mínimas rápido, e só então implemente.

## Design
4. **Puxe o design das fontes oficiais.** Em `design.md`, consulte o HIG / Design Resources
   e registre o que informou cada decisão. Os tokens default são ponto de partida, não fim.
5. **Só use valores da spec na implementação.** Se faltar algo, volte e atualize `design.md`
   (re-aprovando) em vez de improvisar um valor.
6. **Um acento por tela.** Cor sinaliza interação; não decora.
7. **Light + dark sempre.** Cores semânticas que invertem com `prefers-color-scheme`.

## Acessibilidade e forma
8. **Toque ≥ 44px.** Todo alvo interativo.
9. **Contraste ≥ 4.5:1** para texto.
10. **Cantos contínuos ("squircle").** Elevação via translucidez + sombra difusa, não bordas duras.
11. **Deferência.** Sem sombras pesadas, gradientes gratuitos ou chrome que rouba foco.
12. **Movimento com propósito.** 200-400ms, ease-out/spring, e respeite `prefers-reduced-motion`.

## Honestidade técnica
13. **Declare os fallbacks.** SF Pro / New York são licenciadas pra Apple; fora do ecossistema,
    a stack cai no fallback. `backdrop-filter` idem — sempre um fundo sólido de reserva.
14. **Em projeto legado, sinalize e limpe.** Aponte o que briga com o HIG em `design.md §Conflitos`.

## Verificação
15. **Feche com o checklist.** `verify.md` confere cada critério de aceite e cada item do HIG,
    reportando pass/fail. Sem verde em tudo, não está pronto.
