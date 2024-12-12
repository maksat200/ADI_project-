### README.md

# Анализ данных об участниках Олимпийских игр

Этот проект включает анализ данных о спортсменах, участвовавших в Олимпийских играх, с использованием библиотеки pandas для обработки данных и визуализации с помощью matplotlib и seaborn.

### Структура проекта

1. **Файл данных**: `athlete_events.csv` - содержит данные о спортсменах, соревнованиях, медалях и характеристиках участников.

2. **Файлы кода**:
   - `data_analysis.py` - основной скрипт для анализа данных и визуализации.

### Основные этапы анализа

1. **Распределение возраста участников**: Построение гистограммы возрастов участников с использованием seaborn для визуализации.

   ```python
   plt.figure(figsize=(10, 6))
   sns.histplot(data['Age'].dropna(), bins=30, kde=True, color='skyblue')
   plt.title('Распределение возраста участников')
   plt.xlabel('Возраст')
   plt.ylabel('Количество участников')
   plt.show()
   ```

2. **Топ-10 стран по количеству медалей**: Анализ и визуализация количества медалей по странам.

   ```python
   medals_by_country = data[data['Medal'].notna()]['Team'].value_counts().head(10)
   medals_by_country.plot(kind='bar', color='orange')
   ```

3. **Распределение роста и веса участников**: Визуализация распределения роста и веса участников.

   ```python
   plt.figure(figsize=(10, 6))
   sns.scatterplot(data=data, x='Height', y='Weight', alpha=0.5)
   plt.title('Распределение роста и веса участников')
   plt.xlabel('Рост (см)')
   plt.ylabel('Вес (кг)')
   plt.show()
   ```

4. **Количество медалей по годам**: Построение линии, отображающей количество медалей по годам.

   ```python
   medals_by_year = data[data['Medal'].notna()].groupby('Year').size()
   medals_by_year.plot(kind='line', marker='o', color='green')
   ```

5. **Топ-10 видов спорта по количеству участников**: Анализ и визуализация количества участников в топ-10 видов спорта.

   ```python
   sports_by_participants = data['Sport'].value_counts().head(10)
   sports_by_participants.plot(kind='bar', color='purple')
   ```

6. **Распределение медалей по полу участников**: Визуализация распределения медалей между мужчинами и женщинами.

   ```python
   medals_by_gender = data[data['Medal'].notna()].groupby('Sex').size()
   medals_by_gender.plot(kind='pie', autopct='%1.1f%%', labels=['Женщины', 'Мужчины'], colors=['pink', 'lightblue'])
   ```

7. **Количество участников по сезонам**: Визуализация количества участников в зимних и летних Олимпийских играх.

   ```python
   participants_by_season = data.groupby('Season').size()
   participants_by_season.plot(kind='bar', color=['blue', 'red'])
   ```

8. **Средний возраст медалистов по видам спорта**: Анализ среднего возраста медалистов для топ-10 видов спорта.

   ```python
   average_age_by_sport = data[data['Medal'].notna()].groupby('Sport')['Age'].mean().sort_values(ascending=False).head(10)
   average_age_by_sport.plot(kind='barh', color='teal')
   ```

### Установка и использование

1. Установите необходимые библиотеки:
   ```bash
   pip install pandas matplotlib seaborn
   ```

2. Поместите файл `athlete_events.csv` в папку проекта.

3. Запустите `data_analysis.py` для генерации визуализаций.

### Лицензия

Этот проект открыт для использования в образовательных и исследовательских целях.
