+++
title = "Go"
subtitle = "Общий опыт: 1 год"
tags = ['Languages']
date = 2020-03-23

# For description meta tag
description = "Ready, steady, go!"

# Comment next line and the default banner wil be used.
banner = 'img/go.svg'

+++

Проведя некоторое время на одном только Python, я почувствовал необходимость в относительно низкоуровневом языке с вменяемой потоковой моделью (на уровне операционной системы, без фокусов с `async`/`await` вокруг однопоточного цикла событий). И было бы хорошо, если бы у этого языка была большая и активная экосистема! 😅 Мне не хотелось возвращаться к C++ и связываться с JVM-based языками, так что выбор пал на Go.

На Go я написал пару небольших веб-сервисов, созданных для разрабатываемой e-commerce платформы:

- промежуточный сервис диспетчеризации датасетов между предобработчиками данных, поступающих на вход ML-сервисов (на основе [Fiber](https://gofiber.io/));

- внутренний сервис нагрузочного тестирования (на основе [Vegeta](https://github.com/tsenart/vegeta)).

Опыт был положительный, в дальнейшем мне бы хотелось задействовать Go почаще.

___
# Иллюстрация

- Композиция в целом: постер [«Акиры»](https://en.wikipedia.org/wiki/Akira_(1988_film)) (бешенная скорость и огромное внимание к деталям — это явно про `Go`).

- Надписи: несмотря на то, что название языка Go не связано напрямую с японским, я нахожу интересным тот факт, что он созвучен с 語 (['язык'](http://www.romajidesu.com/kanji/%E8%AA%9E)). «Vegeta» написано согласно [оригиналу](https://dragonball.fandom.com/wiki/Vegeta), «Fiber» написано катаканой в меру моего разумения правил транскрибирования.

- Суслик Go: куртка из [Cyberpunk 2077](https://duckduckgo.com/?q=cyberpunk+2077+samurai+jacket&iax=images&ia=images&iai=https%3A%2F%2Fwww.nycjackets.com%2Fwp-content%2Fuploads%2F2019%2F06%2Frocyberpunk-2077-real-bomber-leather-bwn-jacket-b.jpg), с надписью [«Jaeger»](https://www.jaegertracing.io/) (микросервисный трассировщик) на воротнике и старым логотипом [«Traefik»](https://www.marksei.com/wp-content/uploads/2019/08/Traefik-Logo-720x210.png) (граничный маршрутизатор) на спине.
