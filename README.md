## devtools

1. При логине пользователя на сайте:
    
    Вызывается запрос

    POST' 'https://ilms.itmo.ru/api/accounts/public/auth/jwt/login'
    в котором  в теле запроса передаются поля логина и пароля, а в итоге возвращается 200 ответ при правильных креденщиалс:
    {
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9-PXcFz0cJ0RMtfycs",
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJhYzA1ZjRiMS0zMmQ1LT2bpncDpFypXDgxoCoBDX6D0",
    "token_type": "bearer",
    "user_id": "9c05f4b1-32d5-4f30-ab33-c4c7a010e18c",
    "role": "студент"
    }

2. При входе в личный кабинет
    
    вызывается метод:
    
    Request URL - https://ilms.itmo.ru/api/accounts/users/{id пользователя}
    Request Method - GET

    и возвращается json с данными о пользователе:
    {
        "id": "9c05f4b1-32d5-4f30-ab33-c4c7a010e18c",
        "email": "ПОЧТА ПОЛЬЗОВАТЕЛЯ",
        "is_active": true,
        "is_superuser": false,
        "is_verified": true,
        "first_name": "string",
        "last_name": "string",
        "created_at": "2023-10-20T15:30:17.528928Z",
        "deleted_at": null,
        "middle_name": "string",
        "phone": "string",
        "role": "студент"
    }

3. В  DevTools можно менять html страницы и другие параметры и атрибуты для различных целей. Cмотри видео dev_tools.mp4

## swagger

1. Полученный при логине токен можно использовать для вызова других запросов, передавая токен в Headers

'Authorization: Bearer - eyJhbGciOiJItYcJ0RMtfyc - token'

2. Запросы будут возвращать результат для соответствующего пользователя, чей токен используются для авторизации, например список всех назначенных курсов, а так же карту курса конкретного курса. Смотри видео swagger.mp4

3. При попытке получить доступ к защищенной части API, такой как список всех организаций, обычный пользователь с ролью студент получает ошибку - 403 и сообщение, что информация доступна только пользователям с ролью администратор.

![Попытка получить доступ ко всем организациям пользователем с ролью "студент" ](image.png)