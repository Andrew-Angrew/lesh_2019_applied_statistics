
Описание:
========

Статистика -- это наука про то, как делать выводы на основе данных, подверженных влиянию случайных факторов. Т. е. по сути про то, как не косячить, когда принимаешь решения на основе данных из реальной жизни. Суть основных понятий и методов статистики можно ухватить опираясь только на здравый смысл (ну почти). Правда для этого некоторые факты придется воспринять на веру и удовольствоваться в некоторых местах интуитивными (но надеюсь достаточно наглядными) объяснениями вместо четкого доказательства. Обещаю развлечь слушателей историями про несчастия тех, кто недостаточно хорошо понимает статистику)

---

Материал делится на три части:
* Базовые понятия и методы статистики и как ими пользоваться.
* Байки про аналитику данных ("задачи" на здравый смысл и "физическую интуицию")
* Математическая теория (задачи на теорию вероятностей)
* Эксперименты на компьютере (задачи на программирование)

---

Пререквизиты: теория вероятностей


Примерный план:
===============
Дисклэймер: я в основном буду говорить про большие выборки. Мой личный опыт - это машинное обучние и эксперименты на людях в интернете.

1. Базовые понятия частотной статистики:
    Две гипотезы H0 и H1
    Два типа ошибок (False Positive и False Negative).
    статистики, pvalue
    уровень значимости, мощность теста

    Самопальный тест честности монетки.
    "Двухвостый" и "однохвостый" тест.

    Мораль:
        Чтобы определить pvalue нужна только нулевая гипотеза. Мощность зависит от H1.
        Но в жизни как правило H0 еще можно выдумать, а разных H1 много (например в случае монетки есть много способов,
        насколько она может быть нечестна).
        Чем сильнее эффект, который мы хотим измерить (например "нечестность" монетки) и больше размер выборки тем ниже в среднем получается pvalue и тем больше мощность теста.

    тест Манна-Уитни
        Задача: Статистика манна Уитни и площадь под кривой.
        Задача: Приведите пример таких величин X, Y и Z, что P(Y > X) > 1/2, P(Z > Y) > 1/2 и P(X > Z) > 1/2.
        Упражнение: посторйте эмпирическое распределение статистики Манна Уитни для разных размеров выборок при условии нулевой гипотезы.

    2. Центральная предельная теорема и тест Вальда (Стьюдента).
    Распределения. Квантили.
    Задачи:
        Нарисуйти ф-ции распределения и плотности (если она есть) для следующих случайных величин:
            а) Бернуллиевская
            б) Дискретная случайная величина, принимающая значение a_i с вероятностью p_i
            в) Раномерное на [a, b]
            г) (elder) Сумма двух независимых равномерных на [0, 1]
            д) (elder) Максимум из двух независимых равномерных на [0, 1]
        как распределено pvalue при условии нулевой гипотезы?
        Как сгенерировать на компе сэмпл из случайной величины с ф-цией распределния F, если известно как посчитать F^{-1}?
        (math) Есть два распределения, мы кидаем монетку и если выпал орел сэплируем число из первого распредления, если решка -- из второго. Как выражается ф-ция распределения полученной случайной величины, через ф-ции распределения исходных величин?
        (math) Как изменится ф-ция распределения случайной величины, если к ней добавить
            а) константу?
            б) бернуллиевскую случайную величину с вероятностью единицы равной p?
            в) (можно нечетко) случайную величину раномерно распределенную на (-\epsilon, +\epsilon)? Постройте гистограмму в ноутбуке.
        (elder) Как связаны ф-ция плотности и распределения?

    Суть Центральной предельной теоремы.
    Тест Вальда (Стьюдента).
    Важное замечание: Это годится для больших выборок. С маленькими выбороками этот тест можно применять, если есть оcнования предполагать нормальность распределения.
    Ассимптотическая нормальность. Нормальность в природе. История про булочную.
    Задачи:
        как рассчитать размер эксперимента, чтобы доказать эффект определенной силы?
        (elder) Обобщите рассказанный тест Вальда на случай независимых выборок разного размера.
    Доп. глава:
        Почему вообще говоря матожидание случайной величины нельзя измерить. Петербургский парадокс.
        (старшим) Докажите, что если график функции плотности положительной случайной величины выглядит как прямая в логарифмическом масштабе по обеим осям, то у нее бесконечное матожидание.
        Когда можно?

    3. Примеры неправильного использования стат. тестов:
        История про Френсиса Гальтона (не iid data; как не iid мешает проводить ab-тесты. Флэшмобы в рэйтинговых системах)
        Зависимость данных, зависимый тест Стьюдента, где он нужен и жжет.
            Вопрос: помог бы Гальтону тест зависимый тест Стьюдента?
        Задача:
            Матожидание выборочной дисперсии
            Несмещенная оценка дисперсии.
        Остановка ab-эксперимента по достижению стат. значимости.
        Задача:
            (старшим) Все-таки хочется уметь досрочно отключать особо плохие эксперименты. Предложите честное решение этой проблемы (сколь угодно костыльное и странное)
        Перебор стат. тестов
        Меряем не то: Байки из Канемана про мужей умных женщин и маленькие школы.

    4. Множественные сравнения:
        суть проблемы
        Переобучение в статистике: давайте я подберу гипотезу, которая лучше всего подходит к моим данным, а потом по тем же данным оценю ее статзначимость.
        тупой способ справиться с множественными сравнениями
        статья про давайте pvalue будет 0.005, кризис воспроизодимости.
        "Подозрительные" корреляции ( http://tylervigen.com/spurious-correlations ).

    6. Доверительные интервалы.
        Есть число x, его знаю только я. Чтобы вас запутать я добавляю к нему случайную поправку и сообщаю результат вам. Как вы будете по строить доверительный интервал зная распределение из которого я сэмлировал поправку?
            а) Пусть вам задан уровень значимости \alpha. Опишите все корректные способы построить доверительный интервал.
            б) Пусть я штрафую вас за ошибку в меньшую сторону больше, чем за ошибку в большую. Как тогда выгоднее строить доверительный интервал?

    5. Непараметрическая статистика:
        Бутстреп.
        ? ML различения распределений

    6. Немного про байесовскую статистику:
        Стандартная байка про редкую болезнь
        Карикатура bayesian vs frequentist
        Круто, когда есть prior. Но часто его неоткуда взять.

Задачи
======

В начале Первой мировой войны в униформу британских солдат входила коричневая матерчатая фуражка. Металлических касок у них не было. Через некоторое время командование армии было обеспокоено большим количеством ранений в голову. Было решено заменить фуражку металлической каской. Но вскоре командование было удивлено, узнав, что количество ранений в голову увеличилось. Необходимо заметить, что интенсивность сражений была примерно одинаковой до и после введения касок. Так почему же число ранений в голову увеличилось, когда солдаты стали надевать каски, а не фуражки?

Среднее интервал между автобусами и среднее время ожидания.

Средний размер самолета

Есть несколько независимых экспериментов, как сделать одно pvalue для гипотезы, что где-то эффект есть? (другими словами как настроить оповещение, которое разбудит тебя ночью, если у тебя в проде что-то сломалось)

поэкcпериментировать с такими таблицами 2x2 при помощи тестов хи-квадрат, Фишера и Барнарда


Ссылки и материалы
==================
Видосы:
* Панчин 20 мин в основном про множественные сравнения: [youtube](https://www.youtube.com/watch?v=dcVG0NtZMwE) (вопросы лучше не слушать)
* Ит-Лекториум фкн про ошибки в анализе данных: [youtube](https://youtu.be/BOxC1_xHP9A?t=130). Первые 2-26 минуты до курицы и яйца. Хорошие примеры смещения выборок и намайненных корреляций.
* Ит-Лекториум фкн про аналитику в Яндексе: [youtube](https://youtu.be/dvf_x3V0j88?t=3528). Последняя история про ab-тесты в видео зачетная (последние 10 мин).

[Сборник "подозрительных" корреляций](http://tylervigen.com/spurious-correlations).

Историю про булочную и нормальное распределение можно прочитать в книге "Gamov, Stern. Puzzle-math." (Гамов -- тот самый "физический" Гамов). Или [тут](https://pikabu.ru/story/eshche_raz_o_normalnom_raspredelenii_6213153).

[Группа кафедры матстата в vk](https://vk.com/mathstat_mm). B частности там выложена особенно веселая [pdf-ка про аналитику](https://vk.com/doc821751_493607410?hash=353d43eabb6d5e3592&dl=3be03f004a5d20f2b8).

[википедия](https://en.wikipedia.org/wiki/Data_dredging) про p-hacking

