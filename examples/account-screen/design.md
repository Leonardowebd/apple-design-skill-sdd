# Design — Tela de Conta (iOS)

## Sources consulted
- https://developer.apple.com/design/human-interface-guidelines/color → cores semânticas light/dark
- https://developer.apple.com/design/human-interface-guidelines/materials → recipe do Liquid Glass
- https://developer.apple.com/design/human-interface-guidelines/layout → tap target 44px, listas agrupadas

## Resolved tokens
### Typography
- Stack: `-apple-system, "SF Pro Text", "Helvetica Neue", sans-serif`
- Título da barra 18px, nome 17px, e-mail 14px, linhas 16px.
### Color
- `--accent: #007AFF` (light) / `#0A84FF` (dark) — um único acento.
- `--label: rgba(0,0,0,.85)`; `--label-2: rgba(60,60,67,.6)`.
- `--bg: #F2F2F7`; `--surface: #FFFFFF`.
### Spacing / Layout
- Gutter 16px. Linhas com min-height 44px. Separadores 0.5px recuados.
### Shape / Elevation
- Cartões radius 16-20px (contínuo). Sombra difusa `0 12px 40px rgba(0,0,0,.14)`.
### Liquid Glass
- Barra superior: `rgba(255,255,255,.6)` + `backdrop-filter: blur(20px) saturate(180%)`.
- Fallback: fundo sólido `#FFFFFF` quando `backdrop-filter` não é suportado.
### Motion
- Toques com transição de 200ms ease-out. Respeita `prefers-reduced-motion`.
### Iconography
- Chevrons de navegação em `--label` com baixa opacidade. SF Symbols no app real.

## Component specs
- **Barra (glass)**: back chevron (acento) + título centralizado.
- **Perfil**: avatar circular 52px (acento) + nome + e-mail.
- **Lista agrupada**: 3 linhas navegáveis, separador 0.5px recuado, última sem separador.
- **Botão primário**: acento sólido, texto branco, radius 14px, altura >=44px.

## Conflicts & fallbacks
- Sem SF Pro na web fora do ecossistema Apple → cai no fallback da stack.
- `backdrop-filter` → fundo sólido de reserva.
