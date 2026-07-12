---
version: alpha
name: Cascadia Rising UI
description: Визуальная айдентика мобильной RPG Fallout Cascadia Rising — фосфорный CRT-интерфейс Pip-Boy поверх пепельной пустоши.
colors:
  primary: "#14FE17"
  primary-dim: "#0FA511"
  secondary: "#8C9484"
  tertiary: "#FFB642"
  danger: "#FF4633"
  neutral: "#0B0F0A"
  neutral-raised: "#12180F"
  on-primary: "#0B0F0A"
  paper: "#D8D2C0"
typography:
  h1:
    fontFamily: Overseer Mono
    fontSize: 2rem
    fontWeight: 700
    letterSpacing: 0.04em
  h2:
    fontFamily: Overseer Mono
    fontSize: 1.5rem
    fontWeight: 700
  body-md:
    fontFamily: Wasteland Sans
    fontSize: 1rem
    lineHeight: 1.5
  body-dialog:
    fontFamily: Wasteland Sans
    fontSize: 1.125rem
    lineHeight: 1.6
  label-caps:
    fontFamily: Overseer Mono
    fontSize: 0.75rem
    fontWeight: 600
    letterSpacing: 0.12em
  numeral-hud:
    fontFamily: Overseer Mono
    fontSize: 1.25rem
    fontWeight: 700
rounded:
  none: 0px
  sm: 2px
  md: 6px
spacing:
  xs: 4px
  sm: 8px
  md: 16px
  lg: 24px
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    rounded: "{rounded.sm}"
    padding: 12px
  button-primary-pressed:
    backgroundColor: "{colors.primary-dim}"
    textColor: "{colors.on-primary}"
  button-ghost:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.primary}"
    rounded: "{rounded.sm}"
    padding: 12px
  panel-pipboy:
    backgroundColor: "{colors.neutral-raised}"
    textColor: "{colors.primary}"
    rounded: "{rounded.md}"
    padding: 16px
  tag-skill-check:
    backgroundColor: "{colors.neutral-raised}"
    textColor: "{colors.tertiary}"
    rounded: "{rounded.sm}"
    padding: 4px
  bar-danger:
    backgroundColor: "{colors.neutral}"
    textColor: "{colors.danger}"
  tooltip-paper:
    backgroundColor: "{colors.paper}"
    textColor: "{colors.neutral}"
    rounded: "{rounded.none}"
    padding: 8px
---

## Overview

Ретрофутуризм 1950-х, увиденный через люминофор военного терминала. Интерфейс игры —
диегетический экран Pip-Boy: фосфорно-зелёная типографика на почти чёрном стекле,
скан-линии, лёгкое свечение. Второй визуальный язык — «бумага довоенного мира»:
пожелтевшие плакаты и документы (`paper`) для лора, карт и обучающих карточек.
Контраст двух миров (живой CRT против мёртвой бумаги) — основа айдентики.

## Colors

- **Primary (#14FE17):** фосфорный зелёный — весь текст и графика Pip-Boy, HUD, рамки.
  Единственный «живой» цвет экрана.
- **Primary-dim (#0FA511):** остаточное свечение — нажатые состояния, второстепенные
  линии, неактивные вкладки.
- **Secondary (#8C9484):** пепельный шалфей — мировой UI вне Pip-Boy (подписи над NPC,
  индикатор скрытности), не конкурирует с фосфором.
- **Tertiary (#FFB642):** янтарь аварийных ламп — теги проверок навыков `[Речь 75]`,
  предупреждения, валюта. Использовать скупо: янтарь = «обрати внимание».
- **Danger (#FF4633):** сигнальный красный — только урон, критическое HP, враждебность
  фракции. Никогда не для декора.
- **Neutral (#0B0F0A) / Neutral-raised (#12180F):** стекло выключенного и включённого
  CRT; вся глубина строится этими двумя тонами плюс свечением, не тенями.
- **Paper (#D8D2C0):** довоенная бумага — фон записок, карт, слайдов концовок.

## Typography

- **Overseer Mono** (моноширинный, условное имя: класс Monofonto/Share Tech Mono) —
  голос терминала: заголовки, цифры HUD, капс-лейблы. Всегда с трекингом.
- **Wasteland Sans** (гуманистический гротеск высокой читаемости, класс
  Public Sans/Inter) — длинные диалоги и описания: моноширинным читать 350 тысяч слов
  нельзя. `body-dialog` — минимум 1.125rem на телефоне.
- Иерархия строится размером и трекингом, не сменой цвета.

## Layout

- Сетка 8px (`spacing`); зоны касания ≥ 48dp, между соседними целями ≥ 8px.
- Ландшафтная компоновка: сцена по центру, HUD прижат к коротким краям (большие
  пальцы), нижняя треть — диалоги и панель боя.
- Поля прокрутки помечаются градиентным затуханием фосфора, не скроллбарами.

## Elevation & Depth

Теней нет — глубина передаётся свечением: активный слой получает внешний glow
primary на 8%, фон гасится до `neutral`. Модальные окна затемняют сцену на 70%
и добавляют скан-линии — «экран поверх экрана».

## Shapes

Углы почти прямые (`rounded.sm` = 2px — фаска, не скругление). Панели Pip-Boy —
`rounded.md` с двойной линейной рамкой толщиной 1px (`primary-dim` снаружи,
`primary` внутри). Декоративный язык — насечки, риски шкал, перфорация.

## Components

- **button-primary** — единственная заливка фосфором на экране; в один момент времени
  видна максимум одна такая кнопка (главное действие сцены).
- **button-ghost** — все остальные действия: рамка 1px `primary`, фон стекла.
- **tag-skill-check** — янтарные капс-теги проверок в диалогах; серый вариант
  (textColor `secondary`) для недоступных проверок.
- **tooltip-paper** — единственный светлый компонент: лорные подсказки «на бумаге».

## Do's and Don'ts

- **Do:** держать 90% экрана в двух тонах стекла + фосфор; janitor-правило: любой
  третий цвет на экране должен быть тегом внимания (янтарь) или угрозы (красный).
- **Do:** проверки навыков всегда одинаковым паттерном: `[ИКОНКА НАВЫК ПОРОГ]` янтарём.
- **Don't:** тени, градиентные кнопки, скругления > 6px — ломают язык терминала.
- **Don't:** фосфорный зелёный на бумаге (`paper`) и янтарь как декор — только сигнал.
- **Don't:** анимации дольше 200ms в боевом HUD — пошаговый бой должен ощущаться щелчком тумблера.
