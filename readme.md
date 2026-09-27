# Apple Design Skill (Spec-Driven)

Uma skill para agentes de IA (Claude Code, Cursor, Xcode 27, etc.) que gera interfaces no
design system da Apple — Human Interface Guidelines + Liquid Glass — usando **Spec-Driven
Development (SDD)**. Em vez de "gera um estilo Apple aí", o agente escreve a spec, **puxa o
design das fontes oficiais** para tokens concretos, implementa a partir da spec e verifica o
resultado contra o HIG.

> A Apple entregou o design. Esta skill entrega a disciplina para usá-lo direito.

## Por que spec-driven

Pedir "deixa com estilo Apple" para um agente costuma devolver algo que parece Apple à
distância e erra de perto: sombras pesadas, três cores de acento, contraste ruim, cantos
quadrados. Qualidade Apple vem da disciplina do processo, não de copiar CSS.

## O pipeline

```
requirements.md → design.md → tasks.md → implementação → verify.md
```

Cada fase gera um arquivo e termina num **gate de aprovação**. O agente não avança sem o seu OK.

## Instalação

```bash
mkdir -p ~/.claude/skills/apple-design-sdd
cp SKILL.md ~/.claude/skills/apple-design-sdd/SKILL.md
```

## Uso passo a passo

1. **Peça a UI.** "Crie uma tela de login no estilo iOS / Liquid Glass."
2. **Responda o intake.** web ou SwiftUI? iOS ou macOS? projeto novo ou legado? quais telas?
3. **Aprove os requisitos (Gate 1).** Leia `requirements.md`, ajuste, aprove.
4. **Aprove o design (Gate 2).** O agente gera `design.md` com tokens concretos. Revise.
5. **Aprove as tarefas (Gate 3).** `tasks.md` quebra o trabalho em passos rastreáveis.
6. **Deixe implementar.** O agente usa só os valores da spec.
7. **Revise o verify.** `verify.md` confere o resultado contra a spec e o HIG.

## As regras

1. Nunca pule para o código; todo pedido passa pelo pipeline.
2. Um gate por vez; não avance sem aprovação.
3. Puxe o design das fontes oficiais e registre o que informou cada decisão.
4. Só use valores da spec na implementação; se faltar, volte e atualize `design.md`.
5. Um acento por tela.
6. Light + dark sempre, com cores semânticas.
7. Toque ≥ 44px, contraste ≥ 4.5:1, cantos contínuos.
8. Declare os fallbacks (fontes SF, `backdrop-filter`).
9. Em projeto legado, sinalize e limpe o que conflita.

## Licença

MIT. Veja [LICENSE](LICENSE).
