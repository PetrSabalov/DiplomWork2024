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
import matplotlib.pyplot as plt
import seaborn as sns

categories = ['Игрушки', 'Одежда', 'Книги', 'Электроника', 'Парфюмерия']
actividad = [30, 25, 20, 15, 10]  # Проценты покупок в каждой категории

colors = sns.color_palette('pastel')[0:5]

plt.figure(figsize=(8, 6))
plt.pie(actividad, labels=categories, autopct='%1.1f%%', startangle=140, colors=colors)

plt.title('Покупательская активность в новогодние праздники')
plt.axis('equal')  # Для отображения круга

plt.show()

```

![Seaborn Example](https://github.com/PetrSabalov/DiplomWork2024/blob/main/Seaborn_2.png)

### Пример 2: Plotly

```python
import plotly.graph_objects as go
import numpy as np

categories = ['Подарки', 'Еда и напитки', 'Развлечения']
months = ['Декабрь', 'Январь']

expenses = {
    'Подарки': [40, 30],
    'Еда и напитки': [20, 15],
    'Развлечения': [10, 5]
}

x = np.arange(len(months))
y1 = np.array(expenses['Подарки'])
y2 = np.array(expenses['Еда и напитки'])
y3 = np.array(expenses['Развлечения'])


fig = go.Figure()

fig.add_trace(go.Scatter(x=x, y=y1, mode='lines+markers', name='Подарки'))
fig.add_trace(go.Scatter(x=x, y=y2, mode='lines+markers', name='Еда и напитки'))
fig.add_trace(go.Scatter(x=x, y=y3, mode='lines+markers', name='Развлечения'))

fig.add_trace(go.Scatter(
    x=np.concatenate([x, x[::-1]]),  
    y=np.concatenate([y1, y2[::-1]]),  
    fill='toself',  
    fillcolor='rgba(0, 100, 80, 0.2)',  
    line=dict(color='rgba(255, 255, 255, 0)'),  
    name='Подарки и Еда и напитки'
))

fig.update_layout(
    title='Покупательная активность в новогодние праздники',
    xaxis=dict(tickvals=x, ticktext=months),
    yaxis_title='Расходы (млн $)',
    legend=dict(x=0, y=1)
)

fig.show()


```

![Plotly Example]((https://github.com/PetrSabalov/DiplomWork2024/blob/main/Plotly2.png)

### Пример 3: Matplotlib

```python
import matplotlib.pyplot as plt
import numpy as np

years = np.array([2020, 2021, 2022, 2023])
children = np.array([1, 2, 3, 4, 5])
стоимость_подарков = np.array([50, 100, 150, 200, 250])  # Примерные стоимости

prices = np.random.randint(50, 300, size=(len(years), len(children)))

fig, ax1 = plt.subplots()

for i in range(len(years)):
    ax1.plot(children, prices[i], marker='o', label=f'Год {years[i]}')

ax1.set_title('Формирование новогодних цен')
ax1.set_xlabel('Количество детей')
ax1.set_ylabel('Стоимость подарков (руб.)')
ax1.grid()
ax1.legend(loc='upper left')


ax2 = ax1.twinx()
bar_width = 0.15  # Ширина столбцов
x = np.arange(len(children))

ax2.bar(x + bar_width, prices[-1], width=bar_width, color='orange', alpha=0.5, label='Цены 2023')


ax2.set_ylabel('Столбцы: Цены 2023 (руб.)')
ax2.set_xticks(x + bar_width / 2)
ax2.set_xticklabels(children)


ax2.legend(loc='upper right')

plt.show()

```
![Matplotlib Example](https://github.com/PetrSabalov/DiplomWork2024/blob/main/Matplotlib_3.png)

### Пример 3: Seaborn
```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd


data = pd.DataFrame(np.random.rand(5, 5), columns=list('ABCDE'))


correlation_matrix = data.corr()
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm')
plt.title('Корреляционная матрица')
plt.show()
```
![Seaborn Example](https://github.com/PetrSabalov/DiplomWork2024/blob/main/Seaborn_3.png)

### Пример 3: Plotly
```python
import plotly.graph_objects as go

labels = ['Январь', 'Февраль', 'Март', 'Апрель', 'Май', 'Июнь', 'Июль', 'Август', 'Сентябрь', 'Октябрь', 'Ноябрь', 'Декабрь']
category1 = [10, 15, 20, 25, 30, 35, 30, 20, 15, 10, 5, 5]
category2 = [5, 10, 15, 20, 25, 30, 25, 15, 10, 5, 5, 10]
category3 = [2, 5, 8, 12, 15, 20, 15, 10, 5, 3, 2, 2]

# Создание стековой диаграммы
fig = go.Figure()

fig.add_trace(go.Scatter(
    x=labels,
    y=category1,
    mode='lines+markers',
    fill='tozeroy',
    name='Категория 1',
    stackgroup='one'
))

fig.add_trace(go.Scatter(
    x=labels,
    y=category2,
    mode='lines+markers',
    fill='tonexty',
    name='Категория 2',
    stackgroup='one'
))

fig.add_trace(go.Scatter(
    x=labels,
    y=category3,
    mode='lines+markers',
    fill='tonexty',
    name='Категория 3',
    stackgroup='one'
))

fig.update_layout(
    title='Стековая диаграмма покупательной активности',
    xaxis_title='Месяцы',
    yaxis_title='Расходы',
    legend=dict(x=0, y=1)
)

fig.show()

```
![Plotly Example]((https://github.com/PetrSabalov/DiplomWork2024/blob/main/Plotly3.png)

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

Каждая из этих библиотек имеет свои сильные стороны. **Matplotlib** предоставляет огромные возможности для настройки графиков и является основой для других библиотек. **Seaborn** значительно упрощает создание статистических графиков и улучшает внешний вид. **Plotly** идеально подходит для создания интерактивных графиков и визуализации данных в реальном времени.

**Matplotlib, Seaborn** и **Plotly** — это три мощные библиотеки для визуализации данных в Python, каждая из которых обладает своими сильными сторонами:

-	**Matplotlib** — это основа для всех графиков, обеспечивающая максимальный контроль над их настройками и визуализацией. Jбеспечивает наибольшую гибкость и контроль, но требует больше времени и усилий для настройки.
-	**Seaborn** делает процесс построения графиков более удобным и красивым, благодаря высокой абстракции и улучшенным стандартам визуализации. Упрощает создание статистических графиков с качественным дизайном и стильной визуализацией.
-	**Plotly** идеально подходит для создания интерактивных графиков и визуализаций в реальном времени, особенно для веб-приложений. Предлагает исключительные возможности для создания интерактивных и динамичных графиков, идеально подходящих для современных веб-приложений.


Выбор библиотеки зависит от ваших задач и требований к визуализации. Если вам нужно больше контроля и гибкости, используйте **Matplotlib**. Для создания красивых статистических графиков с минимальными усилиями выберите **Seaborn**. Если ваш приоритет — интерактивность и визуализация данных в реальном времени, лучше всего подойдет **Plotly**.
