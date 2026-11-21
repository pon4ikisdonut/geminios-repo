# GeminiOS Official Package Repository (`gem`)

**Official package manifest repository for GeminiOS 1.0 ("Spark")**

Этот репозиторий содержит манифесты пакетов для нативного пакетного менеджера `gem` операционной системы GeminiOS.

## Структура репозитория

- `index.json` — основной индекс репозитория со списком и метаданными всех доступных пакетов.
- `packages/` — манифесты пакетов в формате `.gem.toml`.
- `.github/workflows/publish-repo.yml` — автоматический CI workflow, который валидирует манифесты и пересобирает `index.json` при каждом коммите.

## Доступные пакеты

| Пакет | Версия | Описание |
|---|---|---|
| `geminios-core` | 1.0.0 | Системный брендинг GeminiOS, оптимизации ядра (sysctl) и базовая структура ФС |
| `geminid` | 1.0.0 | Системный демон AI с поддержкой Gemini API, авто-фоллбэком на локальную Gemma и Agent Mode |
| `gemini-cli` | 1.0.0 | Консольный ассистент (`gemini`, `ask`), утилита диагностики `gemini-doctor` и шелл-хуки |
| `gemini-overlay` | 1.0.0 | Material Design 3 Spotlight / AI Agent оверлей (Super+G) и интеграция с Dolphin |
| `gemini-oobe` | 1.0.0 | Интерактивный мастер первого запуска Material Design 3 |
| `geminios-plasma-m3` | 1.0.0 | Тема оформления KDE Plasma 6 в стиле Google Material Design 3 Dark, обои и виджеты |
| `geminios-plymouth` | 1.0.0 | OLED Dark Plymouth экран загрузки |
| `geminios-sddm` | 1.0.0 | Material Design 3 Dark экран входа SDDM на QML |
| `ollama-gemma` | 1.0.0 | Хелпер локальной модели Gemma AI через Ollama под управлением hwcheck |

## Использование в GeminiOS

Конфигурация в `/etc/gem/gem.conf`:

```toml
[repo.geminios-main]
enabled = true
type = "github-manifest"
owner = "pon4ikisdonut"
repo = "geminios-repo"
branch = "main"
base_url = "https://raw.githubusercontent.com/pon4ikisdonut/geminios-repo/main"
index_url = "https://raw.githubusercontent.com/pon4ikisdonut/geminios-repo/main/index.json"
```

Команды управления:

```bash
# Обновить индекс манифестов
sudo gem update

# Поиск пакетов с AI
gem search --ai "video editor"

# Установка пакета
sudo gem install gemini-cli

# Установка из Arch Linux / AUR через мост
sudo gem repo enable arch
sudo gem repo enable aur
sudo gem install arch:neofetch aur:visual-studio-code-bin
```
