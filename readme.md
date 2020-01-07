<p align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Roscosmos_logo_ru.svg/381px-Roscosmos_logo_ru.svg.png"></p>

<h1 align="center">Roscosmos REST API</h1>

<h3 align="center">Open Source REST API по данным космической деятельности корпорации "Роскосмос"</h3>

## Использование

**Пример ответа**

```bash
curl -s http://localhost:8000/api/launchpads/
```

```json
[
    {
        "id": 2,
        "name": "Восточный",
        "establishment_date": "2011-01-01",
        "location": "Россия, Амурская область, г. Циолковский",
        "area": "700 км2",
        "rented": false,
        "used_by": "",
        "use_period": "",
        "no_launches": 5,
        "no_employees": null,
        "description": "Космодром «Восточный» — российский космодром на Дальнем Востоке в Амурской области, вблизи города Циолковского, в 45 км севернее города Свободного и одноименного военного космодрома. Ближайшая железнодорожная станция — «Ледяная». Первый российский гражданский космодром. Общая площадь около 700 км²",
        "image": null
    },
    {
        "id": 3,
        "name": "Плесецк",
        "establishment_date": "1957-01-11",
        "location": "Россия, Архангельская область, г. Мирный",
        "area": "1762 км2",
        "rented": false,
        "used_by": "",
        "use_period": "",
        "no_launches": 1600,
        "no_employees": null,
        "description": "Космодром ПЛЕСЕЦК (1-й Государственный испытательный космодром Министерства обороны Российской Федерации) – самый северный и один из крупнейших космодромов мира, обеспечивающий часть российских и международных космических программ, связанных с оборонными, а также прикладными, научными и коммерческими пусками непилотируемых космических аппаратов. \r\nКосмодром расположен в Плесецком районе Архангельской области России. На западе территория космодрома ограничена железной дорогой «Москва-Архангельск», на севере — рекой Емца. Общая площадь космодрома составляет 1762 км², протяженность с севера на юг — 46 км, с востока на запад — 82 км.",
        "image": null
    },
    {
        "id": 4,
        "name": "ГКЦ (Куру)",
        "establishment_date": "1968-04-09",
        "location": "Франция, Гвиана, Куру",
        "area": "1200 км2",
        "rented": false,
        "used_by": "",
        "use_period": "",
        "no_launches": 483,
        "no_employees": null,
        "description": "Гвианский космический центр — европейский космодром, расположенный вблизи города Куру во Французской Гвиане (департамент Франции в Южной Америке). Его расположение около экватора обеспечивает 15% преимущество по полезной нагрузке по сравнению с запусками в восточном направлении с американского космодрома на мысе Канаверал и 40% — при запусках с космодрома Байконур. С начала 70-х годов прошлого века ГКЦ используется для запусков КА ракетами-носителями семейства «Ариан». Космодром используется в интересах совместных европейских космических программ. Руководство работой ГКЦ осуществляет Французский национальный космический центр (CNES). При этом космодром финансируется из бюджета Европейского космического агентства (ЕSА) и используется в интересах совместных европейских космических программ.",
        "image": null
    },
    {
        "id": 1,
        "name": "Байконур",
        "establishment_date": "1955-07-02",
        "location": "Казахстан, Кызылординская область, г. Байконур",
        "area": "6717 км2",
        "rented": true,
        "used_by": "Россия",
        "use_period": "до 2050 года",
        "no_launches": 5000,
        "no_employees": 10000,
        "description": "Космодром Байконур — первый и крупнейший в мире космодром, расположен на территории Казахстана, в Кызылординской области между городом Казалинск и посёлком Джусалы, вблизи посёлка Тюратам. Территория космодрома Байконур составляет 6717 км². Космодром Байконур и город с одноименным названием вместе образуют комплекс «Байконур», арендованный Россией у Казахстана на период до 2050 года.",
        "image": null
    }
]
```

## Локальная установка
Запустите следующие команды в терминале:
```bash
docker-compose build
docker-compose up
```

Теперь вы можете запрашивть данные с: http://127.0.0.1:8000/api/

## Технические детали
* Для контейниразации приложения и автоматизации развёртывания - [Docker](https://www.docker.com/)
* Для backend - [Django](https://www.djangoproject.com/) c [django-rest-framework](https://www.django-rest-framework.org/)
* Брокер сообщений - [Redis](https://redis.io/)
* Для автоматизации обновления информации запусков - [Celery](http://www.celeryproject.org/)
* Для парсинга данных - [beautifulsoup4](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
* Все данные хранятся на - [PostgreSQL](https://www.postgresql.org/)

## API
* Космодромы: /api/launchpads/
  * Определенный космодром: /api/launchpads/[id]/
* Разгонные блоки: /api/spacetugs/
  * Определенный разгонный блок: /api/spacetugs/[id]/
* Ракета-носители: /api/launchvehicles/
  * Определенный ракета-носитель: /api/launchvehicles/[id]/
* Запуски: /api/launches/
  * Определенный запуск: /api/launches/[id]/
* Космические аппараты: /api/spacecrafts/
  * Определенный КА: /api/spacecrafts/[id]/
* Орбитальные группировки: /api/orbitalgroupings/
  * Определенная орбитальная группировка: /api/orbitalgroupings/[id]/
* Космические обсерватории: /api/spaceobservatories/
  * Определенный космический обсерваторий: /api/spaceobservatories/[id]/
* Международная космическая станция: /api/spacestations/1/

## FAQ's
* Если у вас есть предложения корректировки данных или вопросы, пшите на email.
* Все данные берутся из свободных источников.
* Мы не являемся частью корпорации "Роскосмос.

## Лицензия
MIT