# Описание запросов и ответов в формате JSON

## 1. Просмотр доступных опций открытия вкладов

**Запрос:**

```json
curl -X POST "https://examplebank.ru/api/deposits/options" \
    -H "Authorization: Bearer abc123xyz" \
    -H "Content-Type: application/json"\
    -d'{
        "clientId": "123456",
        "securityToken": "abc123xyz"
        }'
```

**Ответ:**

```json
{
  "deposits": [
    {
      "id": "dep001",
      "depositName": "Сбережения Плюс",
      "interestRate": 5.5,
      "minPeriod": 12,
      "maxPeriod": 36,
      "minDeposit": 1000,
      "maxDeposit": 500000,
      "sortIndex": 1
    },
    {
      "id": "dep002",
      "depositName": "Оптимальный",
      "interestRate": 4.3,
      "minPeriod": 6,
      "maxPeriod": 24,
      "minDeposit": 500,
      "maxDeposit": 250000,
      "sortIndex": 2
    }
  ]
}
```

## 2. Открытие вклада

**Запрос:**

```json
curl -X POST "https://examplebank.ru/api/deposits/open" \
    -H "Authorization: Bearer securityToken" \
    -H "Content-Type: application/json"\
    -d'{
        "clientId": "123456",
        "securityToken": "abc123xyz",
        "id": "001",
        "period": 24,
        "deposit": 15000
        }'

```

**Ответ:**

```json
{
  "status": "success",
  "message": "Вклад успешно открыт",
  "operationId": "op123456",
  "depositId": "dep123456",
  "timestamp": "2024-04-21T12:00:00Z",
  "startDate": "2024-04-21",
  "endDate": "2026-04-21",
  "percentProfit": 5.5,
  "totalAmmount": 15975
}

```

## 3. Просмотр списка открытых вкладов

**Запрос:**

```json
curl -X POST "https://examplebank.ru/api/deposits/all" \
    -H "Authorization: Bearer abc123xyz" \
    -H "Content-Type: application/json"\
    -d'{"clientId": "123456"}'

```

**Ответ:**

```json
{
  "deposits": [
    {
      "depositId": "dep123456",
      "depositName": "Сбережения Плюс",
      "percentProfit": 5.5,
      "totalAmmount": 15975
    },
    {
      "depositId": "dep123458",
      "depositName": "Сбережения Экстра",
      "percentProfit": 5.8,
      "totalAmmount": 105975
    }
  ]
}

```
## 4. Просмотр подробной информации о конкретном открытом вкладе

**Запрос:**

```json
curl -X POST "https://examplebank.ru/api/deposits/info" \
     -H "Authorization: Bearer abc123xyz" \
     -H "Content-Type: application/json"\
-d'{"clientId": "123456","depositId": "dep123456"}'

```

**Ответ:**

```json
{
  "depositId": "dep123456",
  "timestamp": "2024-04-21T12:00:00Z",
  "startDate": "2024-04-21",
  "endDate": "2026-04-21",
  "percentProfit": 5.5,
  "totalAmmount": 15975
}

```
