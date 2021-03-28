+++
title = "C/C++"
subtitle = "Общий опыт: 4 года"
tags = ['recipe']
date = 2020-03-21

# For description meta tag
description = "В погоне за минимальным оверхэдом."

# Comment next line and the default banner wil be used.
banner = 'img/cpp.svg'

+++

Поскольку я начинал с микроконтроллеров, Си является моим первым "серьёзным" языком. Но в какой-то момент мне стало интересно, как писать нативные десктопные GUI, и как не писать один и тот же код для разных типов и структур...

# RTOS

На C++ я разрабатывал самописную [RTOS](https://en.wikipedia.org/wiki/Real-time_operating_system) жёсткого реального времени, использующуюся в системе управления винтокрылого [БПЛА](https://ru.wikipedia.org/wiki/%D0%91%D0%B5%D1%81%D0%BF%D0%B8%D0%BB%D0%BE%D1%82%D0%BD%D1%8B%D0%B9_%D0%BB%D0%B5%D1%82%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9_%D0%B0%D0%BF%D0%BF%D0%B0%D1%80%D0%B0%D1%82). Несмотря на распространённое мнение, что "у C++ слишком большой оверхэд для микроконтроллеров, тем более для обеспечения жёсткого реального времени" всё умещалось и обеспечивалось (`-nostdlib` сыграл не последнюю роль), и в системе были все необходимые абстракции для работы прикладных программ.

До этого, уже на Си, я работал с [FreeRTOS](https://freertos.org/), которую использовал для разработки систем управления импульсными преобразователями и прошивки радиомодема для группировки спутников [Iridium](https://www.iridium.com/), предназначавшегося для установки на БПЛА.

# DSP

Поскольку встраиваемые ОС, с которыми я работал, были написаны на C и C++, цифровая обработка сигналов ([DSP](https://en.wikipedia.org/wiki/Digital_signal_processing)) для нужд систем управления также писалась на соответствующих языках. В основном это были сильно упрощённые библиотеки по линейной алгебре и матанализу для реализации различных фильтров: [Калмана](https://en.wikipedia.org/wiki/Kalman_filter), [эллиптических](https://en.wikipedia.org/wiki/Elliptic_filter), [КИХ](https://en.wikipedia.org/wiki/Finite_impulse_response), [БИХ](https://en.wikipedia.org/wiki/Infinite_impulse_response).

# Имитационная модель

В ходе работы над системой управления БПЛА я также разрабатывал имитационную модель вертолёта, которая должна была, в том числе, работать с полноценными "железными" версиями блоков управления ([HIL](https://en.wikipedia.org/wiki/Hardware-in-the-loop_simulation)). Работа делалась на основе [adevs](https://web.ornl.gov/~nutarojj/adevs/) с использованием интеграторов из [SUNDIALS](https://computing.llnl.gov/projects/sundials) и линейной алгебры из [Blaze](https://bitbucket.org/blaze-lib/blaze/src/master/).

# Qt

До того, как перейти на web-based решения (см. [Python](/ru/skills/python)), я некоторое время разрабатывал интерфейсы для испытательного оборудования на Qt. Слишком много писанины для простого набора кнопок, переключателей и графиков...

___
# Иллюстрация

- Композиция в целом: обложки культовых книг издательства Addison-Wesley по C++ от Скотта Майерса и The "Gang of Four": [Design Patterns](https://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612/), [Effective C++](https://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/), [More Effective C++](https://www.amazon.com/More-Effective-Improve-Programs-Designs/dp/020163371X/), [Effective STL](https://www.amazon.com/Effective-STL-Specific-Standard-Template/dp/0201749629/).

- It's dangerous to go alone! Take [this](https://zelda.fandom.com/wiki/Triforce).

- Пожалуй, каждый, кто бывал в краях C++, захаживал на [мельницу секретаря комитета стандартизации C++](https://herbsutter.com/).

- "Elements of Overcomplicated Designs" — это личное 😄

- Магический квадрат: поскольку на обложке "Design Patterns" изображены ["Лебеди" Эшера](https://arthive.com/escher/works/200315~Swans), мне хотелось поместить на свою квазиобложку что-то близкое по духу. В итоге, выбор пал на магический квадрат из ["Меланхолии I" Дюрера](https://en.wikipedia.org/wiki/Melencolia_I) — то же математическое очарование, тот же гравюрный стиль...
