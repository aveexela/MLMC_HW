# MLMC_HW
Homework projects for HSE Monte Carlo and ML course

Алексеева Валентина Андреевна


# Исследовательский проект: Метод Монте-Карло для оценки устойчивости моделей машинного обучения

## Цель работы

Целью данного проекта является сравнительный анализ устойчивости регрессионных моделей к случайным вариациям тренировочных данных с помощью метода Монте-Карло (bootstrap sampling).

Задача — выявить, какие модели обладают лучшей стабильностью, точностью и предсказательной способностью при работе с различными типами данных.

## Описание исходных данных

Были выбраны три датасета с различными особенностями:

1. Diabetes (sklearn.datasets.load_diabetes)
442 пациента с диабетом,
10 числовых медицинских признаков.
Цель: спрогнозировать прогрессирование болезни

2. California Housing (sklearn.datasets.fetch_california_housing)
~20,000 объектов недвижимости,
Признаки: доход, количество комнат, география и т.д.
Цель: медианная стоимость жилья

3. Energy Efficiency (UCI ML Repository)
768 зданий.
Метрики -- геометрические и конструктивные признаки зданий
Цель: теплопотери при отоплении (Heating Load)

## Используемые методы и обоснование

Все признаки были стандартизированны

Метод Монте-Карло:
Используется bootstrap sampling на тренировочных данных
Для каждой модели выполняются n симуляций (30, 50, 100, 150)
Для каждой симуляции строится модель и делается предсказание

Вычислено:

* Среднее предсказание
* Стандартное отклонение
* Доверительный интервал

## Используемые модели:

* CatBoostRegressor -- высокая точность, поддержка нелинейных зависимостей, работа с малым объемом
* XGBoostRegressor -- быстрый и мощный бустинг, хорошо масштабируется
* GradientBoosting -- устойчивая точность
* ElasticNet -- линейная модель с регуляризацией (L1 + L2), устойчива к мультиколлинеарности
* Ridge/Lasso -- интерпретируемые линейные методы, полезны для базового анализа

## Оценка качества моделей

Использованные метрики:

* MSE (Mean Squared Error) -- среднеквадратическая ошибка
* R² -- доля объясненной дисперсии

Проанализированно:

* Качество модели без Монте-Карло
* Изменения метрик при увеличении n симуляций
* Вариативность предсказани
* Ширина доверительных интервалов

## Выводы:

* Метод Монте-Карло позволяет количественно оценить устойчивость модели
* Бустинговые модели (CatBoost, XGBoost) демонстрируют наилучшее качество и стабильность
* Линейные модели уступают в точности, но полезны для первичного анализа
* Чем сложнее и больше данные, тем выраженнее эффект Монте-Карло

