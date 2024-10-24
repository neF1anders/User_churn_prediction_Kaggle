# Решение задания "Предсказание оттока пользователей (весна 2021)"
Представлена моя версия решения задания с одного из основных открытых соревнований Kaggle - [Предсказание оттока пользователей (весна 2021)](https://www.kaggle.com/competitions/advanced-dls-spring-2021/overview). Выполнено в рамках закрепления практических навыков в работе с основными инструментами в области машинного обучения. Максимальная точность решения на тестовых данных составила 85,3%.
## Содержание
- [Технологии](#технологии)
- [Использование](#использование)
- [Требования](#требования)
- [Ход решения](#ход-решения)
- [Источники](#источники)

## Технологии
- [Python](https://www.python.org/)
- [NumPy](https://numpy.org/)
- [Pandas](https://pandas.pydata.org/)
- [matplotlib](https://matplotlib.org/)
- [Seaborn](https://seaborn.pydata.org/)
- [CatBoost](https://catboost.ai/en/docs/)
- [scikit-learn](https://scikit-learn.org/stable/)

## Использование
Для использования блокнота нужно воспользоваться Google Collab или установить приложение Jupyter Notebook:
- [Jupyter](https://jupyter.org/)
- [Collab](https://colab.google/)
А также все выше перечисленные библиотеки языка Python (seaborn опционально, но некоторые ячейки с визуализацией данных и их зависимостей без неё не запустятся).


### Требования
Для корректной работы понадобится Python одной из последних версий, а также версии библиотек, подходящие для выбранной Вами версии seaborn (если не используется, последние версии всех библиотек).


## Ход решения
Весь полёт мысли изложен в самом блокноте. Если кратко, после визуализации и чистки данных, я искал параметры, которые можно удалить. В задаче многокритериального принятия решений требуется исключить несущественные параметры, так как они создают "шум". Используя catboost, я обучил первую модель (я хотел сперва потренироваться в использовании именно этой модели). Зафиксировал не слишком хорошие результаты, принялся дальше копать данные. 
Для теста других моделей сделал One-hot-encoding (OHE в блокноте), причем поленился выстраивать зависимость кодировки от истинного значения, так что заменил в лоб несколькими коммандами. Обучил логистическую регрессию, к-ближайших соседей, случайный лес. Применил стэкинг для 3 новых моделей + catboost. Мета-моделью выступила логистическая регрессия, так как принимать решения на основе 4 параметров ей по силам, зачем брать что-то сложнее (ну это виденье алгоритма в моей голове, не претендую на звание мыслителя). Эта модель стала финальной в рамках этого проекта.
Если у Вас есть какие-то мысли или предложения, буду рад их прочитать)


## Источники
- [Соревнование](https://www.kaggle.com/competitions/advanced-dls-spring-2021/overview)
- [Статья](https://habr.com/ru/articles/594077/), после которой заинтересовался CatBoost
- [Статья](https://habr.com/ru/articles/801161/), после которой заинтересовался случайным лесом
- [Статья](https://loginom.ru/blog/imbalance-class), в которой описаны методы, которые я так и не решился применить на практике, так как возникло много вопросов, но она меня почему-то вдохновляла копаться в данных. Может, кому будет интересно)
