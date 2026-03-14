<div align="center">

# <img src="https://cdn-icons-png.flaticon.com/128/5968/5968756.png" height=28 /> Zapret Dyson <img src="https://cdn-icons-png.flaticon.com/128/1384/1384060.png" height=28 />

<img src="https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011-blue?style=for-the-badge&logo=windows" alt="Windows">
<img src="https://img.shields.io/badge/Language-C%2B%2B%20%7C%20DirectX%2011-purple?style=for-the-badge&logo=c%2B%2B" alt="C++">
<img src="https://img.shields.io/badge/UI-ImGui-darkred?style=for-the-badge" alt="ImGui">
<img src="https://img.shields.io/badge/Status-Active-success?style=for-the-badge" alt="Status">

<br>

**Альтернатива консольным утилитам. Аппаратно-ускоренный GUI для обхода DPI блокировок.**

Ускорение Telegram Desktop, YouTube, Discord и полная кастомизация.

Также вы можете материально поддержать оригинального разработчика ядра zapret [тут](https://github.com/bol-van/zapret?tab=readme-ov-file#%D0%BF%D0%BE%D0%B4%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D1%82%D1%8C-%D1%80%D0%B0%D0%B7%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%87%D0%B8%D0%BA%D0%B0).
</div>

> **Zapret Dyson** — это аппаратно-ускоренный графический интерфейс (GUI) и система оркестрации для локального обхода систем глубокого анализа трафика (DPI). 
> 
> В отличие от классических VPN-сетей, утилита не маршрутизирует трафик через сторонние удаленные серверы. Инъекция, фрагментация и модификация сетевых пакетов происходят локально на уровне ядра ОС. Данный подход позволяет обходить провайдерские блокировки, сохраняя 100% пропускной способности канала и оригинальный сетевой пинг.

<div align="center">
  <img width="1400" alt="image" src="https://github.com/user-attachments/assets/9b86098c-e7d2-4186-9624-ec83b148d4e0" />
  <img width="1400" alt="image" src="https://github.com/user-attachments/assets/d51828ff-dbed-4fc6-9e4f-614ba6218dad" />
  <img width="1400" alt="image" src="https://github.com/user-attachments/assets/b35b6feb-d53f-4d49-a49d-4653be120d13" />
  <img width="1400" alt="image" src="https://github.com/user-attachments/assets/c0052c7b-c00f-4ef2-b998-fdd162b49519" />
</div>

<br>

> [!CAUTION]
> ### ФЕЙКИ
> Я не веду никакие другие страницы/группы в телеграм/ютуб каналы.
> Если вы наткнулись на что-то вне этой страницы GitHub, что распространяется от моего лица - **ФЕЙК**.

> [!WARNING]
> ### АНТИВИРУСЫ И РЕАКЦИЯ СИСТЕМЫ
> Программа использует драйвер `WinDivert64.sys` для работы с сетью на уровне ядра ОС. Некоторые антивирусы склонны относить файлы WinDivert к классам повышенного риска. При этом детект обязательно имеет название `WinDivert` или `Not-a-virus:RiskTool.Multi.WinDivert`.
> 
> Это абсолютно нормальное поведение. WinDivert — легитимный инструмент для перехвата трафика. Добавьте папку с утилитой в исключения антивируса для стабильной работы.

> [!IMPORTANT]
> ### БЕЗОПАСНОСТЬ БИНАРНЫХ ФАЙЛОВ
> Весь код начиная с версии v1.9.0 подписывается через `signtool` на этапе Post-Build Event, гарантируя подлинность и целостность исполняемого файла. Количество ложных срабатываний Windows Defender сведено к минимуму (Stealth Mode).

---

## 🔥 Что нового в обновлении v1.9.0

- <ins>**UI & VISUAL REVOLUTION**</ins>
  - **Полный контроль в трее:** Сворачивание в системный трей с контекстным меню.
  - **Floating-панель настроек:** Вызывается по клику на шестеренку в хедере, не перекрывая интерфейс.
  - **Глобальный редизайн:** Плавные анимации (`Slide-In / Slide-Out`), эффект Typewriter в ABOUT, RGB-слайдеры для акцентного цвета.
  - **Система частиц:** 4 режима фоновой анимации (`Off`, `Snow`, `Matrix`, `FCK RKN`) с мгновенным переключением.

- <ins>**TELEGRAM ACCELERATION & CRYPTOGRAPHY**</ins>
  - **Native Telegram SOCKS5:** Встроенный сервер на чистом C++ (WinHTTP API) с нулевой нагрузкой на CPU.
  - **AES-CTR Дешифрация (MTProto):** Аппаратная расшифровка ключей через Windows BCrypt для безошибочной маршрутизации.
  - **Мгновенный TCP-Fallback:** Автоматическое переключение на Raw TCP-мост при блокировке WebSocket. Никаких «вечных подключений».
  - **One-Click Setup:** Кнопка автоматического применения прокси прямо в Telegram Desktop.

- <ins>**SYSTEM CORE**</ins>
  - **Интеллектуальная персистентность:** Автосохранение конфигураций при закрытии и сворачивании.
  - **Реальный TCP Ping:** Асинхронный пинг без фризов интерфейса.
  - **Встроенный редактор списков:** Вкладка **LISTS** для управления доменами прямо в GUI.

## 🚀 Архитектура и Оптимизация

Проект полностью исключает необходимость использования командных оболочек (CMD/PowerShell) при повседневной эксплуатации.

* **Стек технологий:** Разработано на чистом C++ (DirectX 11 + ImGui). Исполняемый файл требует права Администратора (манифест `requireAdministrator`) для работы с WinDivert API.
* **Smart UI Synchronization:** Интерфейс умеет «общаться» с ядром Windows. При запуске он сканирует активные службы и автоматически восстанавливает статусы и галочки.
* **Zero-Delay & High-Priority:** Процесс инициализируется с флагом `HIGH_PRIORITY_CLASS`. Потребление CPU в простое — **0%**. Внедрен алгоритм защиты от TCP-фрагментации `ReadExactly`.

## 🛠️ Технический функционал

* **Адаптивная фильтрация (Smart Profiles):** 7 преднастроенных векторов атаки на DPI (Classic, Aggressive, Mobile, Failsafe) для разных провайдеров (Ростелеком, Дом.ру, Уфанет, мобильные сети).
* **Фоновая интеграция (Windows Services):** Бесшовная инсталляция в системные службы. Обход и Telegram Proxy работают невидимо на уровне ОС.
* **VoIP & Game Mode:** Выделенное правило маршрутизации для портов **1024-65535 (TCP/UDP)**. Предотвращает потерю пакетов в играх и чинит <img src="https://cdn-icons-png.flaticon.com/128/5968/5968756.png" height=14 /> Discord.
* **Обход DNS-блокировок:** Динамическая подмена заголовков `Host` и `Origin` (SNI Spoofing).

## ⚙️ Использование: Ускорение Telegram

**Вариант 1. Локальный запуск (Работает, пока открыто приложение):**
1. Перейдите во вкладку **SETTINGS**.
2. Включите **Enable TG Bypass** (запуск на порту 1080).
3. Нажмите **Apply proxy to Telegram**. Согласитесь на применение в открывшемся Telegram.

**Вариант 2. Автозапуск и Фоновый режим (Рекомендуется):**
1. Включите **Enable TG Bypass**.
2. Нажмите **Install Native Service**.
3. Программа установит системные службы. Теперь окно можно закрыть на крестик — прокси работает автономно!

## 🗒️ Добавление адресов прочих ресурсов

Управлять списками маршрутизации теперь можно прямо из вкладки **LISTS** в интерфейсе программы.
Физически текстовые файлы лежат в папке `lists/`:
- **`list-general.txt`** — для доменов (поддомены учитываются автоматически).
- **`list-google.txt`** — для специфичных сервисов и исключений.
- **`list-exclude-user.txt`** / **`ipset-exclude-user.txt`** — для исключения доменов/IP из фильтрации.

## 📌 Принципы продукта

1. **Производительность:** Нулевое влияние на базовую задержку сети.
2. **Изолированность:** Модификация заголовков (SNI, TLS) производится исключительно на локальном ПК без сторонних серверов.
3. **One-Click Deployment:** Трансформация сложных консольных параметров в интуитивный графический интерфейс.

## ⭐ Поддержка проекта

Вы можете поддержать проект, поставив :star: этому репозиторию (сверху справа этой страницы).

<a href="https://star-history.com/#dysonbehind/zapret-discord-youtube&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=dysonbehind/zapret-discord-youtube&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=dysonbehind/zapret-discord-youtube&type=Date" />
   <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=dysonbehind/zapret-discord-youtube&type=Date" />
 </picture>
</a>

## ⚖️ Лицензирование

Проект распространяется на условиях лицензии [MIT](https://github.com/dysonbehind/zapret-discord-youtube/blob/main/LICENSE.txt)

## 🩷 Благодарность участникам

[![Contributors](https://contrib.rocks/image?repo=dysonbehind/zapret-discord-youtube)](https://github.com/dysonbehind/zapret-discord-youtube/graphs/contributors)

💖 Отдельная благодарность разработчику [zapret](https://github.com/bol-van/zapret) - [bol-van](https://github.com/bol-van)
