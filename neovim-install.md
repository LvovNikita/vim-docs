# Установка Neovim + LazyVim для JS/TS

## Требования

- Neovim >= 0.9
- Node.js (для LSP)
- Git

## 1. Установка зависимостей

```bash
sudo apt install ripgrep fd-find fzf
```

- `ripgrep` — быстрый поиск текста по проекту
- `fd` — быстрый поиск файлов
- `fzf` — fuzzy finder

## 2. Установка LazyVim

```bash
git clone https://github.com/LazyVim/starter ~/.config/nvim
rm -rf ~/.config/nvim/.git
```

## 3. Первый запуск

```bash
nvim
```

При первом запуске LazyVim автоматически скачает все плагины.
Когда установка завершится — нажми `q`.

## 4. Установка LSP для JS/TS

Внутри Neovim выполни:

```
:MasonInstall typescript-language-server eslint-lsp prettierd
```

- `typescript-language-server` — автодополнение, go-to-definition, ошибки
- `eslint-lsp` — линтер
- `prettierd` — форматтер

## 5. Проверка

Открой любой TS-файл:

```bash
nvim test.ts
```

Напиши `const x: string = 123` — должна появиться красная подсветка ошибки.

Проверить активные LSP-серверы:

```
:LspInfo
```

## Структура конфига

```
~/.config/nvim/
├── init.lua              # точка входа (не трогай)
└── lua/
    └── plugins/          # сюда добавляй свои плагины
```

## Spell checker (русский + английский)

LazyVim включает spell checker по умолчанию. Чтобы он корректно проверял русский,
добавь в `~/.config/nvim/lua/config/options.lua`:

```lua
vim.opt.spelllang = { "ru", "en" }
```

При первом открытии файла Neovim предложит скачать русский словарь — соглашайся (`y`).
Словарь скачается автоматически с vim.org.

## Mason (менеджер LSP)

Открыть: `:Mason`

| Клавиша | Действие         |
|---------|------------------|
| `/`     | поиск пакета     |
| `i`     | установить       |
| `u`     | обновить         |
| `X`     | удалить          |
| `q`     | закрыть          |
