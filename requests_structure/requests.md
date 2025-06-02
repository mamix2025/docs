## POST /api/register
Content-Type: application/json

**запрос**
{
    "login": "user123",
    "password": "securePass123!",
    "phone": "+79001234567",  // можно интом сделать хз пока
    "full_name": "Fomgleb",
    "email": "fomglebasik@gmail.com"
}

**ответ**
{
    "success": true,
    "user_id": 101,
    "message": "User registered successfully"
}


## POST /api/login
Content-Type: application/json

**запрос**
{
    "login": "user123",
    "password": "hash_of_password" // или забить и хранить просто пароль
}

**ответ**
{
    "success": true,
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}


## POST /api/requests
Content-Type: application/json
Authorization: Bearer <token>

**запрос**
Пустой(т.к. manager_id извлекается из jwt bearer токена)

**ответ**
{
    "requests": [
        {
            "request_id": 501,
            "address": "ул. Ленина, д. 10, кв. 25",
            "apartment_id": 25,
            "type": "протечка воды", // можно попробовать юзать и type_id??
            "status": "assigned",
            "created_at": "2024-05-20T14:30:00Z",
            "resident_name": "Иванов Иван"
        }
    ],
    "total": 15
}


## POST /api/requests/create
Content-Type: application/json
Authorization: Bearer <token>

**запрос**
{
    "apartment_id": 25,
    "type": "поломка лифта",  // или type_id
    "description": "Лифт не реагирует на кнопки 3 этажа",
    "photo_url": "https://example.com/photo1.jpg"  // опционально
}

**ответ**
{
    "success": true,
    "request_id": 502
}

## POST /api/requests/delete
Content-Type: application/json
Authorization: Bearer <token>

**запрос**
{
    "request_id": 1
}

**ответ**
{
    "success": true,
    "message": "Request 1 deleted successfully"
}

## POST /api/requests/change_status
Content-Type: application/json
Authorization: Bearer <token>

**запрос**
{
    "request_id": 1,
    "status_id": 2
}

**ответ**
{
    "success": true
}
