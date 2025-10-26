Вариант 10
2. Предварительный анализ данных
Описательные статистики:
Sales: среднее = 7.50, std = 2.82, min = 0.00, max = 16.27
Price: среднее = 115.80, std = 12.29, min = 24.00, max = 191.00
Advertising: среднее = 6.61, std = 6.65, min = 0.00, max = 29.00

Графический анализ:
- Отрицательная связь между Sales и Price
- Положительная связь между Sales и Advertising
- Качество размещения товара (ShelveLoc) влияет на уровень продаж
- Наивысшие продажи наблюдаются при качестве размещения "Хорошее"

Корреляционный анализ:
Sales & Price: -0.44 (умеренная отрицательная)
Sales & Advertising: 0.27 (слабая положительная)
Price & Advertising: -0.10 (очень слабая отрицательная)

3. Проверка на нормальность

Тест Шапиро-Уилка:
Sales: Statistics=0.99, p=0.3251 - распределение нормально
log_Sales: Statistics=nan, p=1.0000 - распределение нормально


4. Спецификация моделей
fit_lm_0 = β₀ + β₁·Price + β₂·Advertising + β₃·ShelveLoc_Good + β₄·ShelveLoc_Medium 
fit_lm_1 = β₀ + β₁·Price + β₂·Advertising + β₃·ShelveLoc_Good + β₄·ShelveLoc_Medium
fit_lm_2 = β₀ + β₁·Price + β₂·Advertising + β₃·ShelveLoc_Good + β₄·ShelveLoc_Medium + β₅·Price_ShelveLoc_Good
fit_lm_3 = β₀ + β₁·Price + β₂·Advertising + β₃·ShelveLoc_Good + β₄·ShelveLoc_Medium + β₅·Advertising_ShelveLoc_Good
fit_lm_4 = β₀ + β₁·Price + β₂·Advertising + β₃·ShelveLoc_Good + β₄·ShelveLoc_Medium + β₅·Price_ShelveLoc_Good + β₆·Advertising_ShelveLoc_Good
Модели для log_Sales аналогичны

5. Оценка точности моделей
Лучшая модель для Sales: fit_lm_0, MSE_loocv = 3.33
Лучшая модель для log_Sales: fit_lm_3_log, MSE_loocv = 1.383

6. Лучшая модель fit_lm_3_log:
MSE на тестовой выборке = 8.54
Константа: 3.37
Коэффициенты:
Price: -0.017 (увеличение цены на 1 единицу снижает продажи на 0.017 тыс. шт.)
Advertising: 0.03 (увеличение рекламного бюджета на 1 тыс. долл. увеличивает продажи на 0.03 тыс. шт.)
ShelveLoc_Good: 0.87 (качество "Хорошее" увеличивает продажи на 0.87 тыс. шт. относительно "Плохого")
ShelveLoc_Medium: 0.221 (качество "Среднее" увеличивает продажи на 0.221 тыс. шт.)
Advertising_ShelveLoc_Good: -0.019 (взаимодействие рекламы и качества "Хорошее" снижает логарифм продаж на 0.0193)
