# Requirements — Tela de Conta (iOS)

## Context
- Surface: web (HTML/CSS), demonstrando o padrão iOS.
- Platform metaphor: iOS.
- New project (exemplo standalone da skill).
- Scope: uma tela de Conta com perfil + lista de ajustes agrupada.

## User stories
- As a usuário, I want ver e editar minha conta, so that eu gerencio meu perfil sem sair do app.

## Acceptance criteria (EARS)
- WHEN a tela abre THE SYSTEM SHALL mostrar o perfil e uma lista agrupada com toque >=44px.
- WHILE em dark mode THE SYSTEM SHALL inverter as cores semânticas automaticamente.
- WHEN o usuário toca "Salvar alterações" THE SYSTEM SHALL usar o acento único da tela.

## Design intent
- Deve parecer nativo iOS: clareza, deferência, profundidade. Liquid Glass só no chrome.

## Out of scope
- Backend, persistência, navegação entre telas.
