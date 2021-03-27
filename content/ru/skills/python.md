+++
title = "Python"
subtitle = "Общий опыт: 6 лет"
tags = ['Languages']
date = 2020-03-24

# For description meta tag
description = "Нечто совершенно иное."

# Comment next line and the default banner wil be used.
banner = 'img/python_v2.svg'

+++

Для меня Python является естестественным выбором в случаях, когда решаемая проблема не имеет жёстких требований по быстродействию или должна быть выполнена как можно скорее для проверки какой-либо идеи.

# Web-фреймворки

Из всего многообразия Python'овских web-фреймворков мне довелось плотно поработать с тремя:

- [FastAPI](https://fastapi.tiangolo.com/) оказался очень удобным фреймворком, из коробки использующим нативную Python'овскию типизацию во имя runtime валидации (pydantic), всестороннюю асинхронность (ASGI) и интеграцию с `pytest`, а Dependency Injection позволяет решить большую часть проблем с передачей контекста без необходимости устанавливать кучу узкоспециализированных плагинов. На данный момент является моим основным выбором для веб-сервисов на Python.

- [Django](https://www.djangoproject.com/) использовался мной в случаях, когда нужно было быстро сделать самостоятельное приложение "со всеми удобствами". Однако при переходе к микросервисам весь этот обвес вроде шаблонов, админки и авторизации/аутентификации оказывался лишним грузом, да и необходимость всё время ставить хоть и мега-удобный, но внешний REST Framework невольно наводила на мысль: "А почему бы сразу не использовать фреймворк, заточенный под REST?.." Да тот факт, что Django, похоже, в принципе не светит стабильный [асинхронный ORM](https://docs.djangoproject.com/en/3.1/topics/async/#async-safety), способствовал смотреть в сторону других решений.

- [Flask](https://flask.palletsprojects.com/en/1.1.x/) использовался мной при построении REST-сервиса для системы диагностики (на фронте был задействован React). В связи с последующим открытием для себя FastAPI, к Flask я больше не возвращался и сейчас я помню о нём лишь то, что на каждый чих (SQLAlchemy, Jinja...) Flask'у нужно ставить специальный плагин, а приложения нужно дробить на blueprint'ы...

# ORM и базы данных

В Python я зачастую работал с БД через ORM [SQLAlchemy](https://www.sqlalchemy.org/) и Django, иногда используя и SQLAlchemy Core. Сырые SQL-запросы, конечно, незаменимы при оптимизации производительности в условиях растущих нагрузок на сервис, однако, если сервис действительно испытывает такого рода проблемы, вероятно, стоит пересмотреть выбор Python как языка для реализации такого сервиса...

Мне также интересно было поэкспериментировать с библиотеками, позволяющими использовать блага асинхронности, вроде [Tortoise](https://tortoise-orm.readthedocs.io/en/latest/), [GINO](https://python-gino.org/) или [databases](https://www.encode.io/databases/). Однако после выхода [SQLAlchemy 1.4](https://www.sqlalchemy.org/blog/2021/03/15/sqlalchemy-1.4.0-released/), в которой поддержка `asyncio` через `asyncpg` и `aiomysql` официально получила стабильный статус, они несколько утратили актуальность.

# GraphQL

Это творение Facebook'овской инженерной мысли за последние годы набрало значительную популярность, так что я не мог оставаться в стороне, особенно в свете решения вечной проблемы сопряжения интерфейсов с фронтэндом!

Несмотря на очевидное доминирование JavaScript в этой области, экосистеме Python тоже есть что предложить:

- [Graphene](https://graphene-python.org/) — одна из первых Python-библиотек для реализации GraphQL API. Попользовавшись ей некоторое время, я пришёл к выводу, что дополнительный слой между GraphQL-схемами и ORM — так себе идея. Ранее Starlette имела встроенную поддержку Graphene, [теперь всё](https://github.com/encode/starlette/pull/1135).

- [Ariadne](https://ariadnegraphql.org/) — более молодая библиотека, чем Graphene, исправляющая главный её недостаток: GraphQL-схема напрямую парсится из language-agnostic файлов с GraphQL-схемами. Я использовал Ariadne вместе со [Starlette](https://ariadnegraphql.org/docs/starlette-integration), работало норм (за исключением `Dataloader`, о котором ниже).

- [Strawberry](https://strawberry.rocks/) — очень свежая библиотека на основе [Python'овского ответа struct'ам](https://docs.python.org/3/library/dataclasses.html). На момент ознакомления документация была вся в затычках, так что трогал бегло. Очень интересно будет попробовать, когда 🍓 дозреет.

Самая большая проблема со всеми этими библиотеками — отсутствие автоматического кэширования запросов посредством [dataloader'ов](https://github.com/graphql/dataloader). В сыром виде есть решения и для Ariadne, и для Graphene (для Raspberry недавно вроде даже [полноценное решение](https://strawberry.rocks/docs/features/dataloaders) появилось), но спрягать всё это дело с DB-слоем всё ещё не очень приятно, особенно в условиях постоянно меняющихся GraphQL-схем.

# Качество кода

Несмотря на все усилия Гвидо сделать так, чтобы одна проблема решалась одним способом, Python очень лоялен к стилю кода.

Я стараюсь пользоваться [типизацией](https://docs.python.org/3/library/typing.html) и контролировать типы статическими анализаторами вроде [mypy](https://github.com/python/mypy) и [Pyright](https://github.com/microsoft/pyright) (кстати, последний очень даже неплох и как [LSP сервер](https://github.com/emacs-lsp/lsp-pyright) — попроворнее [palantir'овского](https://github.com/palantir/python-language-server) точно).

Линтеры — [flake8](https://flake8.pycqa.org/en/latest/) хватает за глаза, на [pylint](https://www.pylint.org/) в какой-то момент забил.

Поскольку я считаю тесты обязательным элементом CI, [pytest](https://docs.pytest.org/en/stable/) мой бро 😄 ([qutebrowser](https://qutebrowser.org/) от того же типа тоже 🔥)

# Machine Learning/Data Science

Pytorch весит гиг, но есть torchvision и [pretrained-models](https://github.com/Cadene/pretrained-models.pytorch#installation)
Установка Keras постоянно валилась из-за отсутствующих системных зависимостей
Keras/TF+gym, pandas

Анализ фидов на ML (сопоставление)
Система управления БПЛА на ML (DDPG, Deep Deterministic Policy Gradient)
Анализ преобразователей (pandas)

Не нравится Notebook workflow.

___
## Иллюстрация

Чтож, я не ожидал испанской инквизиции!

На создание этой иллюстрации у меня ушло больше времени, чем на всё остальное! (не вместе взятое) Изначально, я хотел сделать коллаж в духе аппликативных анимаций Терри Гильяма с отсылками к бесподобным ["Священному Граалю"](https://en.wikipedia.org/wiki/Monty_Python_and_the_Holy_Grail) и ["Житию Брайана"](https://en.wikipedia.org/wiki/Monty_Python's_Life_of_Brian) и той куче библиотек, что мне довелось использовать:

![Python version 1](/img/python.png)

Но мне не понравился результат. Точнее то, как он смотрелся в общем контексте. В итоге, я решил, что нужно [нечто совершенно иное](https://en.wikipedia.org/wiki/And_Now_for_Something_Completely_Different). Сказано — сделано! 😅
