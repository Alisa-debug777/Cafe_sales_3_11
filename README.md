# Cafe Sales & Performance Analysis (2023)

Цей репозиторій містить проєкт з аналізу продажів кав'ярні: від очищення даних у Python до побудови інтерактивного дашборду в Tableau.
### Що показує дашборд

| **KPI** | Виторг 84 868,50 · середній чек 8,92 · кількість замовлень 9 514 |
| **Sales by Item** | Виторг по товарах, від найбільшого до найменшого: Salad 18 220, Sandwich 14 424, Smoothie 14 096, Juice 11 118, Cake 10 890, Coffee 7 532, Tea 5 161,5, Cookie 3 427 |
| **Revenue by Month** | Виторг по місяцях 2023 року: найкращий червень (7 353), найслабший лютий (6 644) |
| **Payment & Location** | Теплова матриця «спосіб оплати × локація» (виторг), включно з категорією Unknown |
| **Avg Check by Day of Week** | Середній чек по днях тижня (8,72–9,20), вихідні виділено світлішим кольором |

### Фільтри

Дашборд інтерактивний: виторг і графіки перераховуються за вибором **Location** (In-store, Takeaway, Unknown), **Payment Method** (Cash, Credit Card, Digital Wallet, Unknown) і діапазоном дат **Transaction Date**.

### Основні висновки з дашборда

- Три товари (Salad, Sandwich, Smoothie) дають понад половину виторгу; Cookie і Tea найслабші.
- Виторг по місяцях стабільний: різниця між найкращим і найгіршим місяцем близько 10%, лютий коротший за інші.
- Середній чек майже однаковий у всі дні тижня, тож різниці між будніми й вихідними немає.
- Найбільші комірки матриці належать категорії Unknown (невідомі оплата й локація), тому висновки по цих розрізах стосуються лише відомої частини даних.

## 📂 Структура репозиторію

cafe_sales_3_11/
├── README.md
├── data/
│   ├── dirty_cafe_sales.csv
│   └── project_cafe_sales_clean.csv
├── notebooks/
│   ├── cafe_sales.ipynb
│   └── requirements.txt
└── tableau/
    └── dashboard.twbx

Cafe Sales & Performance Dashboard 2023

Focus on top performers: Salad, Sandwich and Smoothie generate 55% of revenue (46,740 of 84,869). Keep them in stock at peak hours and feature them on the menu.
Lift the weakest items: Cookie (3,427) and Tea (5,162) sell the least. Test combo deals with top sellers (e.g. "Sandwich + Cookie") or review their prices.
No weekday or weekend gap: the average order value stays between 8.72 and 9.20 every day, and monthly revenue stays within about ±6% of the average. Weekday-specific staffing or promotions are not supported by this data.
Improve data capture: 31% of revenue has an unknown payment method and 40% an unknown location. Record both at checkout so future analysis can cover the full picture.

