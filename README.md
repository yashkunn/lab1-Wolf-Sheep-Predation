## Комп'ютерні системи імітаційного моделювання
## СПм-23-5, **Лобач Яків Вадимович**
### Лабораторна робота №**1**. Опис імітаційних моделей та проведення обчислювальних експериментів

### Варіант 7, [Wolf Sheep Predation](https://www.netlogoweb.org/launch#http://www.netlogoweb.org/assets/modelslib/Sample%20Models/Biology/Wolf%20Sheep%20Predation.nlogo)

### Вербальний опис моделі:
Ця модель досліджує стабільність екосистеми хижак-жертва. Система вважається нестабільною, якщо вона призводить до вимирання одного або кількох видів, і стабільною, якщо вона підтримує чисельність протягом тривалого часу, незважаючи на коливання популяцій.

### Керуючі параметри:
- **model-version** – вибір моделі: вовки та вівці, або вовки, вівці та трава
- **initial-number-wolves** – початкова кількість вовків
- **initial-number-sheep** – початкова кількість овець
- **sheep-gain-from-food** – кількість енергії, яку отримують вівці від трави
- **wolf-gain-from-food** – кількість енергії, яку отримують вовки від кожної з'їденої вівці
- **grass-regrowth-time** – час, необхідний для відростання трави
- **wolf-reproduce** – ймовірність розмноження вовків
- **sheep-reproduce** – ймовірність розмноження овець
- **show-speed** – відображення рівня енергії вовків та овець

### Внутрішні параметри:
- **max-sheep** – максимальна кількість овець до заповнення всього поля
- **speed** – енергія вівці або вовка
- **countdown** – час до відростання трави після її поїдання вівцею

### Показники роботи системи:
- Популяція овець не перевищує значення max-sheep.
- Вовки підтримують популяцію овець у допустимих межах.
- Чисельність овець достатня для виживання виду й вовків.

### Примітки:
При стандартних налаштуваннях параметрів вовки не встигають контролювати популяцію овець, і приблизно на 330 кроці симуляції вівці заповнюють поле, завершаючи симуляцію з повідомленням "The sheep have inherited the earth".

### Недоліки моделі:
У реальному світі вівці намагалися б уникнути атаки вовка, що могло б змінити результати симуляції. Варто додати ймовірність невдачі при полюванні вовка.

---

## Обчислювальні експерименти

### 1. Дослідження залежності популяції вовків від насиченості однією вівцею
Досліджується вплив насиченості однією вівцею на зростання/зменшення популяції вовків шляхом зміни параметра **wolf-gain-from-food**.

Інші параметри:
- **initial-number-wolves** 50
- **initial-number-sheep** 100
- **sheep-gain-from-food** 4
- **grass-regrowth-time** 30
- **wolf-reproduce** 5%
- **sheep-reproduce** 4%

| Насиченість від вівці | Середня кількість вовків |
|-----------------------|--------------------------|
| 15                    | 34                       |
| 20                    | 75                       |
| 25                    | 93                       |
| 30                    | 89                       |
| 35                    | 92                       |
| 40                    | 92                       |
| 45                    | 68                       |
| 50                    | 24                       |
![image](https://github.com/user-attachments/assets/159c44e9-6899-4d53-bf44-1c6c4c0016a3)

Висновок: стабільна система досягається при значеннях насиченості вовка від 20 до 40. За межами цього діапазону популяція вовків або вимирає від голоду, або надмірно зростає і знищує овець.

### 2. Вплив часу росту трави на популяцію овець
Досліджується залежність зростання/зменшення популяції овець від часу відновлення трави, змінюючи **grass-regrowth-time**.

Інші параметри:
- **initial-number-wolves** 50
- **initial-number-sheep** 100
- **sheep-gain-from-food** 4
- **wolf-reproduce** 5%
- **sheep-reproduce** 4%
- **wolf-gain-from-food** 20

| Час росту трави | Популяція овець |
|-----------------|-----------------|
| 10              | 604             |
| 20              | 191             |
| 30              | 157             |
| 40              | 153             |
| 50              | 150             |
| 60              | 129             |
![image](https://github.com/user-attachments/assets/4f9dea59-1dc2-4307-ac06-448fa90905c3)

Висновок: зі збільшенням часу росту трави популяція овець зменшується, що вказує на залежність зростання популяції від швидкості відновлення їжі.

### 3. Вплив ймовірності появи нової вівці на популяцію вовків
Досліджується залежність зростання/зменшення популяції вовків від вірогідності появи нових овець, змінюючи **sheep-reproduce**.

Інші параметри:
- **initial-number-wolves** 50
- **initial-number-sheep** 100
- **sheep-gain-from-food** 4
- **wolf-reproduce** 5%
- **wolf-gain-from-food** 20
- **grass-regrowth-time** 30

| Вірогідність появи нової вівці | Популяція вовків |
|--------------------------------|------------------|
| 2                              | 43               |
| 4                              | 69               |
| 8                              | 123              |
| 16                             | 203              |
| 20                             | 224              |
![image](https://github.com/user-attachments/assets/47a0a3d1-6ce4-4db5-b234-56a6363c7f49)
Висновок: зі збільшенням ймовірності появи нової вівці, зростає й популяція вовків, оскільки з'являється більше їжі для підтримки їхньої чисельності.
