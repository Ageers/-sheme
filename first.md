
# Алгоритм обработки папки

## Блок‑схема

```mermaid
flowchart TD
    A[Начало] --> B[Получить folder_id из POST]
    B --> C[Присвоить category = null]
    C --> D{folder_id ≠ null?}
    D -- Да --> E[Подготовить SQL-запрос]
    E --> F[Выполнить запрос с folder_id]
    F --> G[Получить результат в folder]
    G --> H{folder существует?}
    H -- Да --> I[Присвоить category = folder.category]
    I --> J[Конец]
    H -- Нет --> K[Выбросить исключение: Папка не найдена]
    K --> J
    D -- Нет --> J
