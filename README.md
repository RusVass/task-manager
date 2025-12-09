# Task Manager API

Простий REST API для задач на Express + MongoDB з базовою авторизацією та Swagger UI.

## Стек
- Node.js, Express
- MongoDB (Mongoose)
- Swagger UI (`/api/docs`)
- Nodemon для дев-запуску

## Запуск локально
1) Встановити залежності:
```
npm install
```
2) Створити `.env`:
```
MONGODB_URI="your-mongodb-uri"
PORT=3000
```
3) Старт:
```
npm run dev
```

## Маршрути
Базовий URL: `http://localhost:3000` (або порт з `.env`).

### Auth (без Basic)
- `POST /api/auth/register` — body: `{"username","email","password","role"}`.
- `POST /api/auth/login` — body: `{"email","password"}`.

### Tasks (потрібен Basic Auth)
Заголовок: `Authorization: Basic <base64(email:password)>`.
- `POST /api/task` — створити задачу; body: `{"description": "..."}`.
- `GET /api/task` — задачі поточного користувача.
- `GET /api/task/all` — усі задачі (роль admin).
- `GET /api/task/:id` — отримати задачу.
- `PUT /api/task/:id` — оновити; body: `{"description": "...", "completed": true|false}`.
- `DELETE /api/task/:id` — видалити.

### Документація
- Swagger UI: `GET /api/docs`.

## Корисні команди
- `npm run dev` — запуск з nodemon.
- `npm run lint:check` / `npm run lint:fix`.
- `npm run format:check` / `npm run format:write`.

## Нотатки
- Змінні середовища обовʼязкові: `MONGODB_URI`, `PORT`.
- База заповнюється користувачами/задачами лише через API (нема сидів).***

