# C4, уровень 1 — System Context

## Диаграмма

```mermaid
graph TB
    subgraph consumers["Кто обращается к платформе"]
        reader["Читатель — человек<br/>читает статьи"]
        author["Автор — человек<br/>пишет и публикует статьи"]
        crawler["Поисковый / превью-краулер — внешняя система<br/>индексирует HTML, берёт Open Graph"]
    end

    site["SSR-платформа блога вроде Medium<br/>рассматриваемая система<br/>серверный рендер готового HTML"]

    subgraph externals["Внешние системы платформы"]
        notify["Сервис уведомлений<br/>push и email подписчикам"]
        media["Медиа-хранилище<br/>картинки статей в S3, раздача через CDN"]
    end

    reader -->|"GET страницы, HTTPS"| site
    crawler -->|"GET HTML, HTTPS"| site
    author -->|"публикация статьи, HTTPS"| site

    site -->|"событие публикации"| notify
    site -->|"загрузка и раздача картинок, S3 API"| media

    classDef focus fill:#1168bd,stroke:#0b4884,color:#ffffff;
    classDef external fill:#999999,stroke:#6b6b6b,color:#ffffff;
    classDef person fill:#08427b,stroke:#052e56,color:#ffffff;
    class site focus;
    class crawler,notify,media external;
    class reader,author person;
```

## Пояснения

Центр — SSR-платформа, наша зона ответственности. Сверху — кто обращается к
платформе: читатель и превью-краулер получают готовый HTML (краулер важен для SEO
и Open Graph — драйвер D2), автор пишет и публикует статьи (драйвер D3).

Снизу — внешние системы, к которым платформа обращается сама, но которые не входят
в её границы:

- **Сервис уведомлений** — платформа шлёт события (например, «автор опубликовал
  статью»), а сервис рассылает push и email подписчикам.
- **Медиа-хранилище** — картинки статей платформа держит не в своей БД, а в
  объектном хранилище (S3) и раздаёт через CDN.

Как платформа устроена внутри (SSR Service, внутренние API), на этом уровне не
раскрывается — детали на уровне [Containers](c4-container.md).
