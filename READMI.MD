# Сравнительный анализ библиотек визуализации данных: Matplotlib, Seaborn и Plotly

## Введение

Matplotlib, Seaborn и Plotly — это три популярных библиотеки для визуализации данных в Python, каждая из которых имеет свои особенности.
Мы изучим их функциональность, возможности и особенности, а также предоставим рекомендации по выбору наиболее подходящей библиотеки для различных задач.


**Основная цель работы:** Провести сравнительный анализ библиотек визуализации данных Matplotlib, Seaborn и Plotly.

## Краткий обзор библиотек

### Matplotlib
**Описание:** Основная библиотека для построения графиков в Python.
  **Основные особенности:*
- Большая гибкость и контроль над графиками.
- Может быть сложно использовать для более сложных визуализаций.
- Хорошо подходит для статичных графиков.
**Области применения:** Научные исследования, инженерия, создание статических отчетов.

### Seaborn
**Описание:** Построен на основе Matplotlib, позволяет легко создавать более красивую и сложную визуализацию
  **Основные особенности:**
- Упрощает работу с статическими данными и интерактивными графиками.
- Подходит для визуализации статистических данных благодаря встроенной функциональности для построения взаимосвязей (например, парные графики, тепловые карты).
**Области применения:** Научные исследования, анализ данных.

### Plotly
**Описание:** Библиотека для создания интерактивных графиков, доступных через веб-браузер.
  **Основные особенности:**
- Позволяет легко создавать графики, которые можно настраивать и зумировать.
- Отлично подходит для больших наборов данных и визуализаций в реальном времени.
- Позволяет экспортировать интерактивные графики в HTML.
**Области применения:** Бизнес-аналитика, веб-разработка, создание интерактивных отчетов.

## Установка библиотек

Для того чтобы начать работать с данными библиотеками, их необходимо установить на свой компьютер, а для этого, скачайте библиотеки:

1. Для библиотеки Matplotlib:
   ```bash
   pip install matplotlib

2. Для библиотеки Seaborn:
   ```bash
   pip install seaborn 

3. Для библиотеки Plotly:
   ```bash
   pip install plotly

## Примеры визуализаций

### Пример 1: Matplotlib

```python
import matplotlib.pyplot as plt
import numpy as np

data = np.random.randn(1000)

# Создание гистограммы
plt.hist(data, bins=30, alpha=0.7, color='blue', edgecolor='black')
plt.title('Гистограмма случайных данных')
plt.xlabel('Значение')
plt.ylabel('Частота')
plt.grid(axis='y', alpha=0.75)
plt.show()


```
![Matplotlib Example](https://github.com/PetrSabalov/DiplomWork2024/blob/main/Matplotlib_1.png)
### Пример 1: Seaborn

```python
import seaborn as sns
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np

data = np.random.randn(1000)

# Создание диаграммы
sns.histplot(data, bins=5, kde=True)
plt.show()

```

![Seaborn Example](https://github.com/PetrSabalov/DiplomWork2024/blob/main/Seaborn_1.png)

### Пример 1: Plotly
```python
import plotly.express as px
import pandas as pd
import numpy as np

data = np.random.randn(1000)

df = pd.DataFrame(data, columns=['Values'])
fig = px.histogram(df, x='Values', nbins=5)

# Показываем график
fig.show()
```

![Plotly Example]((https://github.com/PetrSabalov/DiplomWork2024/blob/main/Plotly1.png)

### Пример 2: Matplotlib

```python
import matplotlib.pyplot as plt
import pandas as pd

# Пример данных
data = {'Дата': ['2023-01-01', '2023-02-01', '2023-03-01'],
        'USD': [75, 76, 74],
        'EUR': [85, 84, 83]}
df = pd.DataFrame(data)

plt.plot(df['Дата'], df['USD'], label='USD/RUB')
plt.plot(df['Дата'], df['EUR'], label='EUR/RUB')
plt.title('Курс рубля по отношению к валютам')
plt.xlabel('Дата')
plt.ylabel('Курс')
plt.xticks(rotation=45)
plt.legend()
plt.tight_layout()
plt.show()


```
![Matplotlib Example](https://github.com/PetrSabalov/DiplomWork2024/blob/main/Matplotlib_2.png)

### Пример 2: Seaborn

```python
import seaborn as sns

data = {'Дата': ['2023-01-01', '2023-02-01', '2023-03-01'],
        'USD': [75, 76, 74],
        'EUR': [85, 84, 83]}
df = pd.DataFrame(data)

df = pd.melt(df, id_vars=['Дата'], value_vars=['USD', 'EUR'], var_name='Валюта', value_name='Курс')
sns.lineplot(data=df, x='Дата', y='Курс', hue='Валюта')
plt.title('Курс рубля по отношению к валютам')
plt.xticks(rotation=45)
plt.show()

```

![Seaborn Example](https://github.com/PetrSabalov/DiplomWork2024/blob/main/Seaborn_2.png)

### Пример 2: Plotly
```python
import plotly.express as px

data = {'Дата': ['2023-01-01', '2023-02-01', '2023-03-01'],
        'USD': [75, 76, 74],
        'EUR': [85, 84, 83]}
df = pd.DataFrame(data)

df = pd.melt(df, id_vars=['Дата'], value_vars=['USD', 'EUR'], var_name='Валюта', value_name='Курс')
fig = px.line(df, x='Дата', y='Курс', color='Валюта', title='Курс рубля по отношению к валютам')
fig.show()

```

![Plotly Example]((https://github.com/PetrSabalov/DiplomWork2024/blob/main/Plotly2.png)

## Рекомендации по выбору библиотеки

- **Matplotlib:** Для высококачественных статических графиков и сложных визуализаций.
- **Seaborn:** Для удобного создания статистических графиков и работы с Pandas.
- **Plotly:** Для интерактивных графиков и визуализаций, требующих взаимодействия с пользователем.

## Примеры из различных областей

- **Образование:** Анализ успеваемости студентов.
- **Финансовые услуги:** Анализ рыночных тенденций.
- **Торговля и ритейл:** Оптимизация товарных запасов.
- **Спорт и фитнес:** Анализ производительности спортсменов.
- **Государственное управление:** Анализ социальных и экономических показателей.

## Заключение

Каждая из библиотек имеет свои сильные и слабые стороны, и выбор зависит от конкретных задач. Matplotlib подходит для статических графиков, Seaborn — для статистических визуализаций, а Plotly — для интерактивных графиков.

