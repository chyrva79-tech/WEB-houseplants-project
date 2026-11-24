# Словник полів моделі кімнатної рослини

Значення в колонці `name` – це постійні імена полів. Їх однаково використовують атрибути `name` у формах, перевірка даних на JavaScript, інтерфейс TypeScript і ключі JSON під час обміну з API.

## Модель рослини (форми `admin.html` і `admin-edit.html`)

| Поле | name | Тип даних | Елемент | Обмеження |
|---|---|---|---|---|
| Ідентифікатор | `id` | число | hidden | лише у формі редагування |
| Назва рослини | `title` | рядок | text | required, minlength 2, maxlength 60 |
| Код рослини | `plantCode` | рядок | text | required, pattern `[A-Z]{3}-[0-9]{3}`, maxlength 7 |
| Вимоги до світла | `light` | перелік: `bright`, `diffused`, `shade` | select | required, перший пункт порожній |
| Частота поливу, днів | `waterDays` | ціле число | number | required, min 1, max 60, step 1 |
| Максимальна висота, см | `maxHeight` | ціле число | number | необов’язкове, min 5, max 1000, step 5 |
| Дата додавання | `addedAt` | дата (РРРР-ММ-ДД) | date | required, min 2026-01-01, max 2026-12-31 |
| Фото | `image` | URL | url | необов’язкове, maxlength 2048 |
| Опис догляду | `description` | рядок | textarea | required, minlength 10, maxlength 500 |
| Безпечна для тварин | `petSafe` | логічне | checkbox | value="true"; невідмічений прапорець не надсилається |

## Призначення полів

- `id` – номер рослини в каталозі, за яким сервер знає, який запис змінюється.
- `title` – назва рослини, яку бачить відвідувач у картці.
- `plantCode` – короткий внутрішній код, наприклад `MON-001` для монстери.
- `plantCode` – короткий внутрішній код, наприклад `MON-001` для монстери.
- `light` – категорія для фільтрації каталогу за освітленням.
- `waterDays` – раз на скільки днів поливати; за цим полем сортуватимуться картки.
- `maxHeight` – висота дорослої рослини в сантиметрах.
- `addedAt` – дата, коли рослину додали до каталогу.
- `image` – адреса фотографії для картки.
- `description` – короткі поради з догляду.
- `petSafe` – чи можна тримати рослину поруч із котами й собаками.

## Форма відгуку (`details.html`)

| Поле | name | Тип даних | Елемент | Обмеження |
|---|---|---|---|---|
| Ім’я | `authorName` | рядок | text | необов’язкове, maxlength 50, autocomplete="name" |
| Електронна пошта | `email` | рядок (e-mail) | email | required, maxlength 100, autocomplete="email" |
| Телефон | `phone` | рядок | tel | необов’язкове, pattern `\+380[0-9]{9}`, autocomplete="tel" |
| Оцінка | `rating` | ціле число 1–5 | radio × 5 | required, група в `<fieldset>` |
| Складність догляду | `careDifficulty` | ціле число 1–5 | range | min 1, max 5, step 1, value 3 |
| Коментар | `comment` | рядок | textarea | required, minlength 20, maxlength 1000 |
| Згода з правилами | `agree` | логічне | checkbox | required |