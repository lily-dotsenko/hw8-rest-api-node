# Description
This project is the Node.js backend part of an educational  project. It provides connection to DB, implements CRUD operations and sends responses to requests. 
## Setup
To set up the project, first run `npm install` then you can start server using `npm start -- --p 5000 --cp 3000` or `node index.js --p 5000 --cp 3000`, where `--p` is server port and `--cp` is client port. Alternatively, you can use .env file to configure the ports. The variables in the `.env` file are `PORT`and `CLIENT_PORT`. In order to obtain a configuration file, you can rename the [.env.example](./.env.example) into `.env`. 

Good luck!

## Homework 8 — REST API

Навчальний застосунок запущено локально: Node.js + Express, база даних SQLite (`softserve.db`).
Frontend: [React repository](https://github.com/lily-dotsenko/hw8-rest-api-react).

### Запуск у Windows PowerShell

Виконати з папки backend (потрібні Node.js та npm):

```powershell
npm.cmd install
npm.cmd start -- --p 5000 --cp 3000
```

Backend працює на `http://localhost:5000`; дозволений origin frontend — `http://localhost:3000`.
Залишити цей термінал відкритим під час перевірок. Frontend запускається в окремому терміналі.

### Перевірені операції

Ручні перевірки виконано через curl, React UI та Postman. Результати зафіксовано на скриншотах.

| Запит | Результат |
| --- | --- |
| GET /products | 200, список товарів |
| POST /products | 201, повідомлення та productId |
| GET /products/:id | 200, створений товар |
| PATCH /products/:id | 200, оновлення ціни; перевірено повторним GET |
| DELETE /products/:id | 200, видалення товару |
| GET /products/:id після видалення | 404, Product not found |

Приклад перевірки доступності API:

```powershell
curl.exe -i http://localhost:5000/products
```

### Postman

Імпортувати [HW8_REST_API.postman_collection.json](HW8_REST_API.postman_collection.json).
Колекція містить п'ять збережених запитів у форматі v2.1.

1. Запустити backend і виконати GET списку товарів.
2. Виконати POST з JSON `{"name":"HW8 Postman Test","price":200}`.
3. Взяти `productId` з відповіді та замінити `9` у URL запитів GET за ID, PATCH і DELETE. Товар із тестовим ID 9 вже видалено.
4. Виконати GET за новим ID, потім PATCH з JSON `{"price":250}` і повторити GET: ціна має бути 250.
5. Виконати DELETE та повторити GET за тим самим ID: очікується 404.

Для POST і PATCH використовувати Body → raw → JSON. Експорт містить запити; докази відповідей збережено окремими скриншотами.

Під час встановлення npm повідомив про застарілі залежності та вразливості шаблону. Автоматичне виправлення залежностей не виконувалося; проєкт використано для локального навчального завдання.
