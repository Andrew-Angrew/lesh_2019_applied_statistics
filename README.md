
Описание:
========

Статистика -- это наука про то, как делать выводы на основе данных, подверженных влиянию случайных факторов. Т. е. по сути про то, как не косячить, когда принимаешь решения на основе данных из реальной жизни. Суть основных понятий и методов статистики можно ухватить опираясь только на здравый смысл (ну почти). Правда для этого некоторые факты придется воспринять на веру и удовольствоваться в некоторых местах интуитивными (но надеюсь достаточно наглядными) объяснениями вместо четкого доказательства. Обещаю развлечь слушателей историями про несчастия тех, кто недостаточно хорошо понимает статистику)

---

Материал делится на четыре части:
1. Байки про аналитику данных ("задачи" на здравый смысл и "физическую интуицию")
2. Базовые понятия и методы статистики и как ими пользоваться.
3. Математическая теория (задачи на теорию вероятностей)
4. Эксперименты на компьютере (задачи на программирование)

---

Пререквизиты: теория вероятностей


Примерный план:
===============
Дисклэймер: я в основном буду говорить про большие выборки.  
Мой личный опыт - это машинное обучение и эксперименты на людях в интернете.

## 1. Базовые понятия частотной статистики.
* Две гипотезы H0 и H1 два и типа ошибок (False Positive и False Negative).  
* статистики, pvalue, уровень значимости, мощность теста  
* Самопальный тест честности монетки.  
* "Двухвостый" и "однохвостый" тест.
* Задача:
    * а) Почему доля положительных результатов нашего теста (в среднем) получается меньше заданного нами уровня значимости? (эффект особенно силен при небольшом количестве бросков монетки)
    * б) Чему равна точная вероятность ложно-положительного результата? (напишите формулу или код, который считает эту вероятность).

* Мораль:
    * Чтобы определить pvalue нужна только нулевая гипотеза. Мощность зависит от H1.
    Но в жизни как правило H0 еще можно выдумать, а разных H1 много (например в случае монетки есть много способов,
    насколько она может быть нечестна).
    * Чем сильнее эффект, который мы хотим измерить (например "нечестность" монетки) и больше размер выборки тем ниже в среднем получается pvalue и тем больше мощность теста.

* тест Манна-Уитни

## 2. Немного про байесовскую статистику:
* Стандартная байка про редкую болезнь, [Видео про ошибки в анализе данных][mistakes]
![](/materials/bayesian_vs_frequentist.png)
* Круто, когда есть prior. Но часто его неоткуда взять.

## 3. Доверительные интервалы.
* Основная задача: Есть число x, его знаю только я. Чтобы вас запутать я добавляю к нему случайную поправку и сообщаю результат вам. Как вы будете по строить доверительный интервал зная распределение из которого я сэмлировал поправку?
    * а) Пусть вам задан уровень значимости \alpha. Опишите все корректные способы построить доверительный интервал.
    * б) Пусть я штрафую вас за ошибку в меньшую сторону больше, чем за ошибку в большую. Как тогда выгоднее строить доверительный интервал?

## 4. Центральная предельная теорема и тест Вальда (Стьюдента).
* Распределения. Квантили.
* Гистограммы и эмпирическая ф-ция распределения.
* Суть Центральной предельной теоремы (ЦПТ).
* Тест Вальда (Стьюдента). Формально это параметрический стат тест.
* Важное замечание: Это годится для больших выборок. С маленькими выбороками этот тест можно применять, если есть оcнования предполагать нормальность распределения.
* Ассимптотическая нормальность. Нормальность в природе. История про булочную.
* Доп. глава:
    * Почему вообще говоря матожидание случайной величины нельзя измерить. Петербургский парадокс.
        * Когда все-таки работает ЦПТ?

## 5. Множественные сравнения:
* Суть проблемы. [Мини-лекция от Панчина][panchin].
* Тупой способ справиться с множественными сравнениями (поправка Бонферони)
* Переобучение в статистике: давайте я подберу гипотезу, которая лучше всего подходит к моим данным, а потом по тем же данным оценю ее статзначимость.
* [Статья](https://www.nature.com/articles/s41562-017-0189-z) про давайте pvalue будет 0.005, кризис воспроизодимости.
* Про [подозрительные корреляции][correleations].


## 6. Еще примеры неправильного использования стат. тестов:
* История про Френсиса Гальтона (не iid data; как не iid мешает проводить ab-тесты. Флэшмобы в рэйтинговых системах)
* Зависимость данных, зависимый тест Стьюдента, где он нужен и жжет.
    Вопрос: помог бы Гальтону тест зависимый тест Стьюдента?
* Остановка ab-эксперимента по достижению стат. значимости.
* Перебор стат. тестов
* Меряем не то: Байки из Канемана про мужей умных женщин и маленькие школы.

## 7. Аналитика в жизни.
* Провальные опросы избирателей в 1936 ("The  Literary  Digest") и 1948 ("Chicago Daily Tribune").
* Про приклеивание почтовой марки для отправки ответа
* [Видео про ab-тесты в Яндексе][ya_abt]

## 8. Непараметрическая статистика:
* Использование нервенва Чебышова и других более сложных неравенств для ограниченных распределений.
* Бутстреп.
* (?) различения распределений с помощью ML  

Ссылки и материалы
==================
Видосы:  
* Панчин 20 мин в основном про множественные сравнения: [youtube][panchin] (вопросы лучше не слушать)  
* Ит-Лекториум фкн про ошибки в анализе данных: [youtube][mistakes]. Первые 2-26 минуты до курицы и яйца. Хорошие примеры смещения выборок и намайненных корреляций.  
* Ит-Лекториум фкн про аналитику в Яндексе: [youtube][ya_abt]. Последняя история про ab-тесты в видео зачетная (последние 10 мин).  
* [Яндекс изнутри](https://events.yandex.ru/lib/talks/5559/) про ab-тесты и повышение чувствительности метрик с помощью ML (для взрослых детей).  

[Сборник "подозрительных" корреляций](http://tylervigen.com/spurious-correlations).

Историю про булочную и нормальное распределение можно прочитать в книге "Gamov, Stern. Puzzle-math." (Гамов -- тот самый "физический" Гамов). Или [тут](https://pikabu.ru/story/eshche_raz_o_normalnom_raspredelenii_6213153).

[Группа кафедры матстата в vk](https://vk.com/mathstat_mm). B частности там выложена особенно веселая [pdf-ка с загадками про аналитику][analytical_puzzles].

[википедия](https://en.wikipedia.org/wiki/Data_dredging) про p-hacking


[panchin]: https://www.youtube.com/watch?v=dcVG0NtZMwE
[ya_abt]: https://youtu.be/dvf_x3V0j88?t=3528
[mistakes]: https://youtu.be/BOxC1_xHP9A?t=130
[correleations]: http://tylervigen.com/spurious-correlations
[analytical_puzzles]: https://vk.com/doc821751_493607410?hash=353d43eabb6d5e3592&dl=3be03f004a5d20f2b8
