# SSR-платформа контентного сайта

Сквозной проект курса OTUS «Microservice Architecture».

## Система

Блог-платформа вроде Medium: авторы пишут статьи, читатели открывают их в вебе.
Страницы статей рендерятся на сервере (SSR) и отдаются готовым HTML. Данные
собираются из внутренних сервисов и внешних managed-провайдеров по контрактам, а
готовый HTML кэшируется.

## Драйверы

Приоритеты, на которые ссылаются остальные документы:

- **D1** — резкие всплески трафика на популярной статье;
- **D2** — готовый HTML для поиска и превью соцсетей (SEO + Open Graph);
- **D3** — новые и изменённые статьи автора должны оперативно появляться на сайте;
- **D4** — публичный сайт: простой = потеря трафика.

## Артефакты домашнего задания №2

| Артефакт | Файл |
|----------|------|
| Атрибуты качества | [`docs/01-quality-attributes.md`](docs/01-quality-attributes.md) |
| Дерево полезности + сценарии | [`docs/02-utility-tree.md`](docs/02-utility-tree.md) |
| Компромиссы (trade-offs) | [`docs/03-tradeoffs.md`](docs/03-tradeoffs.md) |
| Диаграммы C4 (Context, Containers) | [`docs/views/`](docs/views/) |
| Запись решения (ADR) | [`docs/adr/0001-use-ssr.md`](docs/adr/0001-use-ssr.md) |

## Артефакты домашнего задания №3

| Артефакт | Файл |
|----------|------|
| Декомпозиция на сервисы (возможности, границы, cohesion/coupling, DIP) | [`docs/04-decomposition.md`](docs/04-decomposition.md) |

## Артефакты домашнего задания №4

| Артефакт | Файл |
|----------|------|
| Рендеринг и доставка (модель рендеринга, code splitting, эффект на LCP/TTFB) | [`docs/05-rendering-delivery.md`](docs/05-rendering-delivery.md) |

## Артефакты домашнего задания модуля 2 (фронт-архитектура)

| Артефакт | Файл |
|----------|------|
| Фронтенд-архитектура (FSD, рендеринг, monorepo vs microfrontend, CI/CD) | [`docs/06-frontend-architecture.md`](docs/06-frontend-architecture.md) |
| Рендеринг и доставка (часть B, общая с ДЗ №4) | [`docs/05-rendering-delivery.md`](docs/05-rendering-delivery.md) |
| ADR: SSR вместо CSR (переиспользуется из ДЗ №2) | [`docs/adr/0001-use-ssr.md`](docs/adr/0001-use-ssr.md) |
| ADR: Feature-Sliced Design как архитектура фронтенда | [`docs/adr/0002-frontend-fsd.md`](docs/adr/0002-frontend-fsd.md) |
| ADR: Фронтенд-монолит вместо микрофронтендов | [`docs/adr/0003-frontend-monolith.md`](docs/adr/0003-frontend-monolith.md) |

## Раскладка репозитория

```
.
├── README.md                       обзор проекта и драйверы
└── docs/
    ├── 01-quality-attributes.md    выбор атрибутов качества под драйверы
    ├── 02-utility-tree.md          дерево полезности и сценарии с метриками
    ├── 03-tradeoffs.md             архитектурные компромиссы
    ├── 04-decomposition.md         декомпозиция на сервисы (DDD)
    ├── 05-rendering-delivery.md    рендеринг и доставка, эффект на LCP/TTFB
    ├── 06-frontend-architecture.md фронт-архитектура (FSD, масштаб, CI/CD)
    ├── views/
    │   ├── c4-context.md           C4, уровень Context
    │   └── c4-container.md         C4, уровень Containers
    └── adr/
        ├── README.md               журнал решений (список ADR)
        ├── 0001-use-ssr.md         SSR вместо CSR
        ├── 0002-frontend-fsd.md    FSD как архитектура фронтенда
        └── 0003-frontend-monolith.md  фронтенд-монолит вместо микрофронтендов
```
