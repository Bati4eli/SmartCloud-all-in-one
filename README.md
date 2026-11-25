<p align="center">
  <img src="docs/smartcloud-banner.png" alt="SmartCloud — коллаж из фотографий" width="100%">
</p>

<h3 align="center">Личное облако для фото и видео с ИИ, который помнит каждый кадр</h3>

<p align="center">
  Снимки с телефона загружаются сами. Сервер находит лица, места, текст и смысл кадра.<br>
  Нужное фото находится за пару касаний — в браузере и на Android.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Java-25-E76F00?style=flat-square&logo=openjdk&logoColor=white" alt="Java 25">
  <img src="https://img.shields.io/badge/Spring_Boot-3.5-6DB33F?style=flat-square&logo=springboot&logoColor=white" alt="Spring Boot 3.5">
  <img src="https://img.shields.io/badge/Groovy-4-4298B8?style=flat-square&logo=apachegroovy&logoColor=white" alt="Groovy 4">
  <img src="https://img.shields.io/badge/gRPC-contract--first-244C5A?style=flat-square&logo=grpc&logoColor=white" alt="gRPC">
  <img src="https://img.shields.io/badge/Kafka-event--driven-231F20?style=flat-square&logo=apachekafka&logoColor=white" alt="Kafka">
  <br>
  <img src="https://img.shields.io/badge/PostgreSQL-PostGIS_·_pgvector-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL + PostGIS + pgvector">
  <img src="https://img.shields.io/badge/Python-CV_·_ML-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Ollama-Qwen_VL-000000?style=flat-square&logo=ollama&logoColor=white" alt="Ollama">
  <img src="https://img.shields.io/badge/Angular-21_·_PWA-DD0031?style=flat-square&logo=angular&logoColor=white" alt="Angular 21">
  <img src="https://img.shields.io/badge/Android-Java-3DDC84?style=flat-square&logo=android&logoColor=white" alt="Android">
  <img src="https://img.shields.io/badge/Docker-Compose-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker">
</p>

<p align="center">
  <a href="#-как-найти-любое-фото">Возможности</a> ·
  <a href="#architecture">Архитектура</a> ·
  <a href="#photo-pipeline">Обработка фото</a> ·
  <a href="#-инженерные-решения">Инженерные решения</a> ·
  <a href="#-репозитории">Репозитории</a>
</p>

---

## 🌟 Коротко

**SmartCloud** — self-hosted фототека полного цикла. Сервер, обработка фото и ИИ-модели работают на своём железе, поэтому снимки не уходят в чужое облако.

<table>
<tr>
<td width="33%" valign="top">

**📲 Загрузка без участия**<br>
Android-клиент сам отправляет новые снимки на сервер. Live-фото сохраняются вместе с видеофрагментом.

</td>
<td width="33%" valign="top">

**🧠 Понимание кадра**<br>
Лица, место съёмки, текст на фото, ИИ-категория и смысловой вектор появляются у фото сразу после загрузки.

</td>
<td width="33%" valign="top">

**🔐 Своё — у себя**<br>
Модели работают локально на GPU. Чувствительные снимки скрываются автоматически. Делиться можно отдельной ссылкой.

</td>
</tr>
</table>

---

## 🔍 Как найти любое фото

У каждого снимка есть несколько признаков: место, люди, альбомы, теги и ИИ-категории. Фильтр можно открыть по любому из них, а потом сузить выборку другими.

```mermaid
mindmap
  root((📸 Фото))
    📍 Геометки
      Карта с кластерами
      Город и адрес
    👤 Лица
      Люди по именам
      Склейка похожих лиц
    🗂️ Альбомы
      Свои подборки
      Альбомы из папок
      Избранное · Видео · Live
    🏷️ Теги
      Свои теги с эмодзи
      Эмодзи подбирает ИИ
    🤖 ИИ-категории
      Море · Еда · Дети
      Документы · Чеки
    🔎 Поиск по смыслу
      «закат у моря»
      Текст на фото
    📅 Время и камера
      Лента по датам
      Камеры и смартфоны
```

<table>
<tr>
<td width="50%" valign="top">

### 📍 Геометки и карта

Все снимки с GPS показаны на карте. Близкие точки собираются в кластеры с превью и счётчиком. Сервер заранее считает кластеры для 15 уровней масштаба, поэтому карта с тысячами фото открывается сразу.

Фото без GPS получают координаты от соседнего снимка, сделанного в то же время. Для каждой точки сервис геокодинга подставляет город и адрес.

</td>
<td width="50%" valign="top">

### 👤 Лица

ИИ находит лица на каждом снимке и собирает фото одного человека в группу. Группе можно дать имя, а потом искать фото по нему.

Похожие группы приложение предлагает объединить или склеивает само. Лишнее лицо можно убрать из группы, а случайного прохожего — скрыть.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🗂️ Альбомы

- **Свои альбомы** — подборки из выбранных фото.
- **Альбомы из папок** сами пополняются, когда в папке появляется новый снимок.
- **Системные альбомы**: избранное, фото, видео, Live-фото и снимки с каждой камеры с логотипом бренда.

</td>
<td width="50%" valign="top">

### 🏷️ Теги

Свой тег ставится на любое фото: «Отпуск 2025», «Дача», «Свадьба Маши». При создании тега ИИ предлагает к нему подходящий эмодзи 🏖️ 🏡 💍. Тег работает как фильтр и как отдельный альбом.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🤖 ИИ-категории

Каждое фото получает категорию без участия пользователя:

`🌊 Море` `🌳 Парки` `🍕 Еда` `🐾 Животные` `👶 Дети` `🖍️ Детский рисунок` `🎉 Праздник` `🚗 Транспорт` `💻 Техника` `👗 Одежда` `🖼️ Картина` `📄 Документы` `🧾 Чеки` `🛂 Паспорт` `▦ Штрихкоды`

Чеки и сканы документов больше не теряются среди снимков из отпуска.

</td>
<td width="50%" valign="top">

### 🔎 Поиск по смыслу

Запрос «закат у моря», «собака на снегу» или «торт со свечами» находит нужные кадры, даже если у фото нет подписей. Запрос можно писать на любом языке.

Поиск учитывает и текст на самих фото: вывески, чеки, страницы документов.

</td>
</tr>
</table>

### 🧩 Фильтры складываются

Любые признаки комбинируются в один запрос. Рядом с каждым вариантом показано, сколько фото останется после его выбора, поэтому пустых выборок не бывает.

```mermaid
flowchart LR
    A(["👤 Мама и Маша"]) --> R
    B(["📍 Крым"]) --> R
    C(["🤖 Море"]) --> R
    D(["📅 Лето 2024"]) --> R
    E(["🔎 «закат»"]) --> R
    R(["✨ 12 фото"])

    classDef chip fill:#FFF4E5,stroke:#FF9800,color:#5D4037
    classDef result fill:#FF9800,stroke:#E65100,color:#fff,font-weight:bold
    class A,B,C,D,E chip
    class R result
```

- **«Любой из»** — фото, где есть Мама *или* Маша.
- **«Все сразу»** — только кадры, где Мама и Маша вместе. Так же работают теги и ИИ-категории.
- Фильтр по альбому, папке, камере, избранному, видео и Live-фото.
- Отфильтрованную подборку можно сразу посмотреть на карте.

### 🎁 И ещё

| Возможность | Как работает |
| --- | --- |
| 👁️ **Скрытие чувствительного** | ИИ отмечает откровенные снимки и прячет их из ленты. Отметку можно поставить или снять вручную. |
| 🔗 **Доступ по ссылке** | Альбом или подборку можно отправить родным, им не нужен аккаунт. |
| 🧹 **Поиск дубликатов** | Приложение находит одинаковые файлы по всей фототеке и помогает удалить лишнее. |
| ♻️ **Корзина** | Удалённые папки восстанавливаются целиком, конфликты имён разбираются заранее. |
| ⚡ **Живые обновления** | Новое фото, найденное лицо или созданный альбом сразу появляются на всех открытых устройствах. |
| 📱 **Web и Android** | Один интерфейс в браузере, в установленном PWA и на телефоне. |

---

<a name="architecture"></a>

## 🏗️ Архитектура

Микросервисы на Java/Groovy и Python, общий gRPC-контракт для всех клиентов, одна база PostgreSQL с гео-индексами и векторами и S3-хранилище для файлов. Общий том между контейнерами один — `processing` для свежих загрузок, пока их обрабатывают.

### Обзор

```mermaid
flowchart TB
    subgraph Clients["Клиенты"]
        direction LR
        Web["🌐 Web / PWA"]
        Android["📱 Android"]
        Desktop["🖥️ Desktop"]
    end

    Nginx["🚪 Nginx · TLS<br/>маршрут по имени метода"]
    Web -->|gRPC-Web · REST| Nginx
    Android -->|gRPC · REST| Nginx
    Desktop -->|gRPC| Nginx

    subgraph Backend["Бэкенд · Java"]
        direction LR
        Api["⚙️ API<br/>метаданные, поиск"]
        Files["📤 Файлы<br/>все байты"]
        Realtime["📡 Живые<br/>события"]
        Worker["🏭 Фоновая<br/>обработка"]
    end

    Nginx --> Api
    Nginx --> Files
    Nginx --> Realtime
    Files -->|очередь| Worker

    AI["🧠 ИИ · Python + GPU<br/>лица, векторы, VLM"]
    Data[("🗄️ PostgreSQL<br/>Redis · S3")]

    Files --> AI
    Worker --> AI
    Api --> Data
    Files --> Data
    Realtime --> Data
    Worker --> Data
```

### Связи внутри бэкенда

```mermaid
flowchart TB
    Nginx["🚪 app-cloud-frontend<br/>Nginx: выбор сервиса<br/>по имени метода"]

    Api["⚙️ app-cloud-api × N<br/>метаданные, альбомы, лица,<br/>теги, поиск, шаринг, вход"]
    Files["📤 app-cloud-file-gateway × N<br/>upload, download, видео,<br/>превью, ZIP; EXIF и превью<br/>загрузки до ответа"]
    Realtime["📡 app-cloud-realtime-gateway × N<br/>subscribe_events, heartbeat"]

    Nginx -->|gRPC метаданных| Api
    Nginx -->|"REST и gRPC с байтами"| Files
    Nginx -->|subscribe_events| Realtime

    Kafka["📨 kafka<br/>свежие загрузки<br/>6 партиций, повторы, DLT"]
    TaskTable[("🗂️ scheduled_tasks<br/>пересчёты, повторы")]
    Files --> Kafka
    Api --> TaskTable

    subgraph Worker["🏭 app-cloud-media-worker × N"]
        direction LR
        Consumer["📨 Kafka-конвейер<br/>лица, автотеги, VLM"]
        Tasks["🗂️ Обработчики задач<br/>ENRICH_MEDIA<br/>LOCATE_MEDIA<br/>RELOCATE_ALL<br/>REBUILD_MAP<br/>EMBED_IMAGES<br/>ANALYZE_AI<br/>FIND_LIVE_VIDEOS<br/>RESCAN / REDETECT /<br/>MERGE_FACES"]
        Jobs["⏱️ Периодические работы<br/>кластеры карты, корзина,<br/>сессии, ANALYZE<br/>ShedLock: одна реплика"]
    end

    Kafka -->|партиции<br/>на реплики| Consumer
    TaskTable -->|SKIP LOCKED| Tasks

    AI["🧠 ИИ · Python + GPU<br/>face-detector<br/>image-embedder<br/>location-preview<br/>ollama · Qwen VL"]
    Data[("🗄️ postgresql<br/>PostGIS · pgvector<br/>🪣 s3-storage<br/>📂 том processing")]
    Redis[("⚡ redis<br/>кэш, канал событий")]

    Files -->|превью, вектор| AI
    Worker -->|лица, VLM,<br/>пересчёты| AI
    Api --> Data
    Files --> Data
    Worker --> Data
    Worker -->|события| Redis
    Redis -.->|в открытые потоки| Realtime
```

Свежая загрузка лежит рабочей копией на томе `processing`. Её читают шлюз файлов, `location-preview` и `face-detector`, а удаляет воркер после фоновой обработки. События клиентам в Redis пишут воркер, API и шлюз файлов. Каждая реплика realtime-gateway отдаёт их в свои открытые потоки. API ещё обращается к VLM за переводом поисковых запросов. Метрики собирают Prometheus и Grafana.

> [!NOTE]
> **Бэкенд разделён по профилю нагрузки.**
> - `app-cloud-api` отвечает на запросы метаданных и не хранит состояния.
> - `app-cloud-file-gateway` передаёт все байты файлов.
> - `app-cloud-realtime-gateway` держит долгие потоки событий.
> - `app-cloud-media-worker` выполняет фоновую обработку.
>
> Каждый сервис масштабируется отдельно и запускается в нескольких репликах. Домены файлов, медиа, лиц и поиска живут в общем ядре `lib-cloud-core`: их связывают общие SQL-запросы и транзакции.

<a name="photo-pipeline"></a>

## 🎞️ Путь одной фотографии

```mermaid
sequenceDiagram
    autonumber
    participant Phone as 📱 Android
    participant FG as app-cloud-file-gateway
    participant K as kafka
    participant W as app-cloud-media-worker
    participant CV as face-detector · location-preview
    participant AI as ai-ollama · image-embedder
    participant DB as postgresql
    participant S3 as s3-storage
    participant RT as app-cloud-realtime-gateway

    Phone->>FG: загрузка нового снимка (gRPC или REST)
    FG->>S3: оригинал целиком
    FG->>CV: путь к рабочей копии: превью
    CV-->>FG: превью байтами
    FG->>S3: превью
    FG->>AI: байты превью: вектор
    FG->>DB: EXIF, место, вектор превью (pgvector)
    FG-->>Phone: ответ на загрузку: превью и EXIF готовы
    FG->>K: задача на фоновую обработку
    K-->>W: задача достаётся одной реплике воркера
    W->>CV: путь к рабочей копии: лица
    CV-->>W: аватары и векторы лиц
    W->>S3: аватары лиц
    W->>AI: байты превью: текст на фото, проверка чувствительности
    W->>DB: лица, категории, кластер карты (PostGIS)
    W->>W: удаляет рабочую копию после конца синхронной части
    W-->>RT: событие через Redis Pub/Sub
    RT-->>Phone: событие в живом потоке — фото обработано
```

## 💡 Инженерные решения

| Решение | Зачем |
| --- | --- |
| **Contract-first gRPC** | Один набор `.proto` порождает код для Java-сервера, TypeScript-клиента (gRPC-Web) и Android. Галереи, лента и события приходят server-streaming'ом, поэтому экран рисуется по мере получения данных. |
| **Одна база вместо трёх** | PostgreSQL + PostGIS + pgvector: гео-запросы, поиск ближайших векторов и фасеты с подсчётом выполняются одним SQL. Отдельные поисковый движок и векторная БД не нужны. |
| **Объектное хранилище** | Файлы лежат в S3 (SeaweedFS) под ключами `{userId}/ORIGINAL/{fileId}`; имена и дерево папок живут только в БД, поэтому переименование и перенос мгновенны. Свежая загрузка до конца обработки лежит рабочей копией на томе `processing`: обработчики читают её с диска, а не скачивают из S3, последний обработчик её удаляет. |
| **Асинхронный конвейер** | Загрузка отвечает сразу, тяжёлая обработка идёт через Kafka. Пересчёт старых фото (новые векторы, перестроение карты) ставится в очередь фоновых задач. |
| **Мультиязычный CLIP** | `jina-clip-v2` переводит фото и текст запроса в одно векторное пространство. Запрос на русском находит кадр без машинного перевода. |
| **Предрасчитанная карта** | Кластеры для 15 уровней масштаба готовятся заранее, карта не считает их на лету. |
| **Локальный ИИ** | Все модели — на своём GPU. Есть профили под 8 и 16 ГБ VRAM. |
| **Одинаковый UX** | Web и Android держат одни тексты, порядок элементов и переходы. Различаются только платформенные жесты и диалоги. |
| **Надёжность** | Миграции Liquibase, интеграционные тесты на Testcontainers, роли и JWT в gRPC, TLS на входе, метрики в Prometheus и Grafana. |

<a name="модели-для-обработки-фото"></a>

### 🧠 Модели

| Модель | Что делает | Где работает |
| --- | --- | --- |
| [InsightFace buffalo_l](https://pypi.org/project/insightface/0.7.3/) | Находит лица и сравнивает их | CPU |
| [jina-clip-v2](https://huggingface.co/jinaai/jina-clip-v2) | Векторы фото и запросов для поиска по смыслу | NVIDIA GPU, ≈1,8 ГБ VRAM |
| [Qwen2.5-VL 3B Instruct Q4_K_M](https://huggingface.co/ggml-org/Qwen2.5-VL-3B-Instruct-GGUF) | Читает текст на фото и определяет чувствительный контент | 8 ГБ VRAM, например RTX 3070 Ti |
| [Qwen3-VL 8B Instruct Q4_K_M](https://huggingface.co/Qwen/Qwen3-VL-8B-Instruct-GGUF) | То же, точнее | 16 ГБ VRAM, например RTX 5070 Ti |

## 📦 Репозитории

| Репозиторий | Назначение | Стек |
| --- | --- | --- |
| [SmartCloud-Backend-apps](https://github.com/Bati4eli/SmartCloud-Backend-apps) | Сервер, обработка медиа, развёртывание | Java 25, Groovy, Spring Boot, Python, gRPC, Kafka, PostgreSQL |
| [SmartCloud-Frontend](https://github.com/Bati4eli/SmartCloud-Frontend) | Веб-клиент, устанавливается как PWA | Angular 21, Material 3, gRPC-Web, Leaflet |
| [SmartCloud-Android](https://github.com/Bati4eli/SmartCloud-Android) | Android-клиент с автозагрузкой | Java, gRPC |
| [SmartCloud-Desktop-MAUI](https://github.com/Bati4eli/SmartCloud-Desktop-MAUI) | Кроссплатформенный клиент, ранний этап | .NET MAUI, gRPC |

Как собрать и запустить каждую часть, описано в README репозиториев: [backend](https://github.com/Bati4eli/SmartCloud-Backend-apps#readme), [web](https://github.com/Bati4eli/SmartCloud-Frontend#readme), [Android](https://github.com/Bati4eli/SmartCloud-Android#readme).

---

<p align="center">
  <img src="docs/smartcloud-icon.png" alt="SmartCloud" width="64"><br>
  <sub>Проект спроектирован и написан <a href="https://github.com/Bati4eli">@Bati4eli</a> — от схемы базы до Android-клиента.<br></sub>
</p>
