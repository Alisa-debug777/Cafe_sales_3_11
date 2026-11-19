
## 📂 Структура репозиторію

<img width="299" height="232" alt="Снимок экрана 2026-11-10 в 21 26 37" src="https://github.com/user-attachments/assets/af8add7a-d9ff-4529-b79b-e1bcd91b99dd" />

# Cafe Sales & Performance Analysis (2023)

Цей репозиторій містить проєкт з аналізу продажів кав'ярні: від очищення даних у Python до побудови інтерактивного дашборду в Tableau.
This repository contains a café sales analysis project: from data cleaning in Python to an interactive dashboard in Tableau.

## Дані та очищення

**Джерело:** Kaggle, Cafe Sales (dirty dataset).
**До очищення:** 10 000 транзакцій, 8 колонок (Transaction ID, Item, Quantity, Price Per Unit, Total Spent, Payment Method, Location, Transaction Date). Усі колонки мали тип `object`, бо в них були слова-помилки.

**Що зроблено:**
- Дублікатів немає (ні повних рядків, ні повторів Transaction ID).
- "ERROR" і "UNKNOWN" (3 256 значень у 7 колонках) замінено на пропуски (NaN).
- Назви колонок приведено до формату `snake_case`; `quantity`, `price_per_unit`, `total_spent` переведено в числа, `transaction_date` у дату.
- Пропущені `item` відновлено за ціною, якщо ціна однозначно визначає товар (489 рядків: 1 → Cookie, 2 → Coffee, 5 → Salad).
- Для цін 3 (Cake / Juice) і 4 (Sandwich / Smoothie) товар визначається неоднозначно: заповнено випадково за часткою кожного товару (474 рядки). Ці рядки позначено `item_guessed = True`. Рейтинг товарів за виторгом без них не змінюється.
- 6 рядків, де товар визначити не вдалося, позначено "Unknown".
- Пропуски в `payment_method` і `location` замінено на "Unknown", бо їх надто багато (32% і 40%), щоб видаляти.
- Видалено рядки без дати, кількості, ціни або суми, які не вдалося відновити.
- Додано колонки: month, month_name, weekday, weekday_name, is_weekend.

**Після очищення:** 9 514 записів. Видалено 486 рядків (4,86%). Пропусків у таблиці немає.

### Що показує дашборд

| **KPI** | Виторг 84 868,50 · середній чек 8,92 · кількість замовлень 9 514 |
| **Sales by Item** | Виторг по товарах, від найбільшого до найменшого: Salad 18 220, Sandwich 14 424, Smoothie 14 096, Juice 11 118, Cake 10 890, Coffee 7 532, Tea 5 161,5, Cookie 3 427 |
| **Revenue by Month** | Виторг по місяцях 2023 року: найкращий червень (7 353), найслабший лютий (6 644) |
| **Payment & Location** | Теплова матриця «спосіб оплати × локація» (виторг), включно з категорією Unknown |
| **Avg Check by Day of Week** | Середній чек по днях тижня (8,72–9,20), вихідні виділено світлішим кольором |

## What the dashboard shows

| Block | Content |
|---|---|
| **KPI** | Revenue 84,868.50 · average order value 8.92 · total orders 9,514 |
| **Sales by Item** | Revenue by item, from highest to lowest: Salad 18,220, Sandwich 14,424, Smoothie 14,096, Juice 11,118, Cake 10,890, Coffee 7,532, Tea 5,161.5, Cookie 3,427 |
| **Revenue by Month** | Monthly revenue in 2023: best month June (7,353), weakest month February (6,644) |
| **Payment & Location** | Heat map "payment method × location" (revenue), including the Unknown category |
| **Avg Check by Day of Week** | Average order value by day of the week (8.72–9.20), weekends highlighted in a lighter color |

### Фільтри / Filters

Дашборд інтерактивний: виторг і графіки перераховуються за вибором **Location** (In-store, Takeaway, Unknown), **Payment Method** (Cash, Credit Card, Digital Wallet, Unknown) і діапазоном дат **Transaction Date**.

The dashboard is interactive: revenue and charts are recalculated based on the selected **Location** (In-store, Takeaway, Unknown), **Payment Method** (Cash, Credit Card, Digital Wallet, Unknown) and the **Transaction Date** range.

### Основні висновки з дашборда / Key insights from the dashboard

- Три товари (Salad, Sandwich, Smoothie) дають понад половину виторгу; Cookie і Tea найслабші.
- Виторг по місяцях стабільний: різниця між найкращим і найгіршим місяцем близько 10%, лютий коротший за інші.
- Середній чек майже однаковий у всі дні тижня, тож різниці між будніми й вихідними немає.
- Найбільші комірки матриці належать категорії Unknown (невідомі оплата й локація), тому висновки по цих розрізах стосуються лише відомої частини даних.

- Three items (Salad, Sandwich, Smoothie) generate more than half of the revenue; Cookie and Tea are the weakest.
- Monthly revenue is stable: the gap between the best and the weakest month is about 10%, and February is shorter than the other months.
- The average order value is almost the same on every day of the week, so there is no difference between weekdays and weekends.
- The largest cells of the heat map belong to the Unknown category (unknown payment method and location), so conclusions for these breakdowns apply only to the known part of the data.

  
Cafe Sales & Performance Dashboard 2023

Focus on top performers: Salad, Sandwich and Smoothie generate 55% of revenue (46,740 of 84,869). Keep them in stock at peak hours and feature them on the menu.
Lift the weakest items: Cookie (3,427) and Tea (5,162) sell the least. Test combo deals with top sellers (e.g. "Sandwich + Cookie") or review their prices.
No weekday or weekend gap: the average order value stays between 8.72 and 9.20 every day, and monthly revenue stays within about ±6% of the average. Weekday-specific staffing or promotions are not supported by this data.
Improve data capture: 31% of revenue has an unknown payment method and 40% an unknown location. Record both at checkout so future analysis can cover the full picture.


