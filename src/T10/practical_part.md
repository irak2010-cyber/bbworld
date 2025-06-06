# Программные измерительные мониторы

## Результаты тестирования

### Задание 1: Измерение времени выполнения

| Алгоритм         | Реальное время (ms) | Использование памяти (MiB) |
|------------------|---------------------|----------------------------|
| Линейный поиск   | 112.5               | 45.7                       |
| Бинарный поиск   | 0.8                 | 38.2                       |

### Задание 2: Измерение использования памяти

Пиковое использование памяти:
- Линейный поиск: 45.7 MiB
- Бинарный поиск: 38.2 MiB

### Задание 3: Анализ результатов

1. **Скорость работы на больших данных**:
   - Бинарный поиск значительно быстрее (0.8 ms vs 112.5 ms)
   - Причина: временная сложность O(log n) у бинарного против O(n) у линейного
   - На массиве из 10 млн элементов бинарный поиск делает максимум ~23 сравнения, тогда как линейный - до 10 млн

2. **Использование памяти**:
   - Бинарный поиск использует немного меньше памяти (38.2 vs 45.7 MiB)
   - Причина: линейный поиск может создавать временные объекты при итерации, тогда как бинарный работает с индексами

3. **Ограничения инструментов**:
   - `time`/`Measure-Command`:
     * Измеряет время выполнения всей программы, а не только целевой функции
     * Может быть неточным для очень быстрых операций
     * Не учитывает "прогрев" интерпретатора Python
   - `memory_profiler`:
     * Добавляет накладные расходы на выполнение
     * Может показывать не все выделения памяти из-за оптимизаций Python
     * Не учитывает память, используемую системными библиотеками

## Выводы

Бинарный поиск предпочтительнее для больших отсортированных данных благодаря:
- Экспоненциально лучшей производительности
- Немного более эффективному использованию памяти
- Однако требует предварительной сортировки данных, что может нивелировать преимущества для однократных поисков
