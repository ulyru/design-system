# Как ИИ-Агентам Использовать Дизайн-Систему Golova

Этот файл можно давать Claude Code, Codex и другим ИИ-агентам перед созданием прототипов Golova.

## Что Это За Продукт

Golova — профессиональная B2B SaaS-платформа для компаний, которые занимаются арендой AV-оборудования и техническим обеспечением мероприятий.

Интерфейс должен ощущаться как современная ERP/CRM-система:

- инженерный;
- профессиональный;
- насыщенный информацией;
- спокойный;
- надежный;
- ориентированный на ежедневную работу.

Не делать лендинг, BI-панель, игровой интерфейс или стартапный промосайт.

## Какие Файлы Читать

1. `AI_USAGE.md` — быстрые правила для ИИ.
2. `tokens.json` — машинно-читаемый контракт токенов.
3. `css/tokens.css` — runtime CSS variables.
4. `css/components.css` — классы компонентов.
5. `index.html` — живая витрина, примеры и правила использования.
6. `DESIGN_SYSTEM_GUIDE.md` — русская памятка по поддержке системы.

## Главные Правила

- Используй CSS-переменные из `css/tokens.css`.
- Не хардкодь цвета в компонентах.
- Для цветов используй semantic tokens: `--text-*`, `--bg-*`, `--border-*`, `--icon-*`.
- Primitive tokens (`--neutral-*`, `--dark-*`, `--brand-*`) используй только при документировании токенов или создании новых semantic tokens.
- Темная тема включается через `.theme-dark` или `[data-theme="dark"]`.
- Не создавай отдельные классы вроде `.button-dark`; компонент должен работать через токены.
- Формы всегда угловатые: `--radius-form` (`4px`).
- Switch track — единственный pill-shaped form control.
- Roboto Flex — весь UI-текст.
- PragmataPro Mono — только логотип и декоративные акценты, не body copy.
- Иконки в HTML-примерах — Bootstrap Icons: `bi bi-*`.

## Визуальный Стиль

Делать:

- плотные рабочие экраны;
- таблицы, списки, панели, формы;
- тонкие разделители;
- спокойную типографическую иерархию;
- минимум теней;
- понятные состояния: default, hover, focus, disabled, error, success.

Не делать:

- большие карточки без необходимости;
- декоративные иллюстрации;
- градиенты;
- тяжелые тени;
- чрезмерное пустое пространство;
- яркую маркетинговую композицию;
- цвет как основной способ иерархии.

## Базовое Подключение

```html
<link rel="stylesheet" href="css/tokens.css">
<link rel="stylesheet" href="css/components.css">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bootstrap-icons/1.11.3/font/bootstrap-icons.min.css">
```

Темная тема:

```html
<html lang="ru" data-theme="dark">
```

или для отдельного блока:

```html
<div class="theme-dark">
  ...
</div>
```

## Компонентные Контракты

### Buttons

```html
<button class="btn btn-md btn-primary">
  <i class="bi bi-plus-lg"></i>
  Создать
</button>

<button class="btn btn-md btn-secondary">
  <i class="bi bi-download"></i>
  Экспорт
</button>

<button class="btn btn-md btn-danger">
  <i class="bi bi-trash3"></i>
  Удалить
</button>
```

Варианты:

- `.btn-primary` — главное действие, обычно одно на экран.
- `.btn-secondary` — второстепенное действие.
- `.btn-informative` — информационное акцентное действие.
- `.btn-danger` — разрушительное действие.
- `.btn-ghost` — низкоприоритетное действие в тулбаре.
- `.btn-link` — действие внутри текста.

Размеры:

- `.btn-sm`
- `.btn-md`
- `.btn-lg`

Icon-only:

```html
<button class="btn btn-md btn-icon-only btn-secondary" aria-label="Ещё">
  <i class="bi bi-three-dots"></i>
</button>
```

У icon-only кнопок всегда нужен `aria-label`.

### Tabs

```html
<div class="tabs">
  <button class="tab active">Все</button>
  <button class="tab">В аренде</button>
  <button class="tab">Резерв</button>
</div>
```

### Forms

```html
<label class="field">
  <span class="field-label">Название компании <span class="req">*</span></span>
  <input class="ctrl" type="text" placeholder="ООО Ромашка">
  <span class="field-hint">Юридическое или рабочее название клиента.</span>
</label>
```

Ошибка:

```html
<label class="field is-error">
  <span class="field-label">Email <span class="req">*</span></span>
  <input class="ctrl" type="email" value="wrong-email">
  <span class="field-error-text"><i class="bi bi-exclamation-circle"></i>Введите корректный email</span>
</label>
```

Input with icon:

```html
<label class="field">
  <span class="field-label">Поиск</span>
  <span class="ctrl-wrap">
    <span class="affix"><i class="bi bi-search"></i></span>
    <input class="ctrl" type="text" placeholder="Артикул или название">
  </span>
</label>
```

Checkbox, radio, switch:

```html
<label class="check">
  <input type="checkbox" checked>
  <span class="box"></span>
  Согласен с условиями
</label>

<label class="radio">
  <input type="radio" name="period" checked>
  <span class="dot"></span>
  Месячный тариф
</label>

<label class="switch">
  <input type="checkbox" checked>
  <span class="track"></span>
  Уведомления включены
</label>
```

### Modal

```html
<div class="modal">
  <div class="modal-header">
    <div>
      <h3>Редактировать позицию</h3>
      <p>Изменения применятся к текущей строке.</p>
    </div>
    <button class="btn btn-sm btn-icon-only btn-ghost modal-close" aria-label="Закрыть">
      <i class="bi bi-x-lg"></i>
    </button>
  </div>
  <div class="modal-body">
    <label class="field">
      <span class="field-label">Название</span>
      <input class="ctrl" type="text" value="Yamaha QL5">
    </label>
  </div>
  <div class="modal-footer">
    <button class="btn btn-md btn-secondary">Отмена</button>
    <button class="btn btn-md btn-primary">Сохранить</button>
  </div>
</div>
```

### Product Card

```html
<article class="pcard">
  <div class="img">
    <span class="badge badge-neutral">Продажа б/у</span>
    <div class="fav">♥</div>
    фото товара
  </div>
  <div class="body">
    <h3 class="title">Акустическая система Yamaha DXR12</h3>
    <p class="price">8 500 ₽ <span class="kit-flag"><i></i>Комплект</span></p>
    <div class="seller"><span class="star">★</span> 4.9 · Pro Sound</div>
    <div class="loc">Москва · самовывоз</div>
    <button class="cta">Подробнее</button>
  </div>
</article>
```

## Prompt Для Claude Code

```text
Перед началом прочитай AI_USAGE.md, tokens.json, css/tokens.css и css/components.css.
Собери прототип Golova как плотный B2B SaaS/ERP экран.
Используй существующие CSS variables и component classes.
Не хардкодь цвета, не делай лендинг, не используй градиенты и декоративные иллюстрации.
Поддержи светлую и темную тему через data-theme="dark".
```

## Когда Можно Отклоняться

Отклонение допустимо только если:

- нужного компонента еще нет в дизайн-системе;
- отклонение явно подписано в прототипе как temporary;
- новый паттерн потом будет перенесен в `index.html` и `css/components.css`.
