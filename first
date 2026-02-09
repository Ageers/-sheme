```mermaid
flowchart TD
    A[Начало] --> B[Присвоить $folder_id:<br>isset($_POST['folder_id']) &&<br>is_numeric($_POST['folder_id']) ?<br>(int)$_POST['folder_id'] : null]
    B --> C[Присвоить $category = null]
    C --> D{ $folder_id ≠ null? }
    D -- Да --> E[Подготовить SQL‑запрос:<br>$stmt = $pdo->prepare('SELECT id, name, category<br>FROM folders WHERE id = ? LIMIT 1')]
    E --> F[Выполнить запрос:<br>$stmt->execute([$folder_id])]
    F --> G[Получить результат:<br>$folder = $stmt->fetch()]
    G --> H{ $folder существует? }
    H -- Да --> I[Присвоить $category = $folder['category']]
    I --> J[Конец]
    H -- Нет --> K[Выбросить исключение:<br>'Папка не найдена']
    K --> J
    D -- Нет --> J
