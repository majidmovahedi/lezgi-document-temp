# 📡 Control Panel API Documentation

---

# 🔔 کنترل بازر (Buzzer)

### Endpoint

```http
POST /buzzer
```

### Request Body

```json
{
  "state": 0
}
```

### Parameters

| مقدار | توضیح |
| ----- | ----- |
| 0     | خاموش |
| 1     | روشن  |

---

# 🚨 کنترل آژیر (Siren)

### Endpoint

```http
POST /siren
```

### Request Body

```json
{
  "state": 1
}
```

### Parameters

| مقدار | توضیح |
| ----- | ----- |
| 0     | خاموش |
| 1     | روشن  |

---

# 🔄 ریست سیستم (System Reset)

### Endpoint

```http
POST /system/reset
```

### Request Body

```json
{
  "command": "RESET"
}
```

### Description

ریست کامل MCU — ممکن است سیستم برای ۱ تا ۲ ثانیه در دسترس نباشد.

---

# 📊 دریافت لاگ‌ها (Logs)

### Endpoint

```http
GET /logs
```

### Description

لیست وضعیت لحظه‌ای دستگاه‌ها و رویدادها.

---

### Response Example

```json
[
  {
    "id": 1,
    "loop": 1,
    "device": "Smoke Detector",
    "address": "Vahed3",
    "status": "NORMAL"
  }
]
```

---

### Fields

| Field   | Type   | Description |
| ------- | ------ | ----------- |
| id      | number | شناسه       |
| loop    | number | شماره لوپ   |
| device  | string | نام دستگاه  |
| address | string | آدرس        |
| status  | string | وضعیت       |

---

### Status Values

| مقدار   | توضیح   |
| ------- | ------- |
| NORMAL  | عادی    |
| ALARM   | هشدار   |
| FAULT   | خطا     |
| DISABLE | غیرفعال |

---


# 📦 دریافت اسلات‌ها (Slots)

### Endpoint

```http
GET /slots
```

---

### Description

لیست تمام لوپ‌ها / ماژول‌ها.

---

### Response Example

```json
[
  {
    "id": 1,
    "name": "لوپ 1",
    "status": "OPEN",
    "loopState": "NORMAL",
    "loopCurrent": 1.8,
    "loopParts": 2,
    "disabled": false,
    "engineeringTest": false,
    "relayDisabled": false,
    "address": "Vahed1",
    "sirenDisabled": false,
    "reset": false,
    "sendToLoop": true
  }
]
```

---

### Fields

| Field           | Type    | Description  |
| --------------- | ------- | ------------ |
| id              | number  | شناسه        |
| name            | string  | نام لوپ      |
| status          | string  | OPEN / CLOSE |
| loopState       | string  | وضعیت فنی    |
| loopCurrent     | number  | جریان        |
| loopParts       | number  | بخش‌ها       |
| disabled        | boolean | غیرفعال      |
| engineeringTest | boolean | تست          |
| relayDisabled   | boolean | رله          |
| address         | string  | آدرس         |
| sirenDisabled   | boolean | آژیر         |
| reset           | boolean | ریست         |
| sendToLoop      | boolean | ارسال دیتا   |

---

### Status Values

| مقدار | توضیح   |
| ----- | ------- |
| OPEN  | فعال    |
| CLOSE | غیرفعال |

---


# ⚡ دریافت وضعیت پاور (Power)

### Endpoint

```http
GET /power
```

---

### Response Example

```json
{
  "batteryVoltage": 12.6,
  "inputVoltage": 220,
  "batteryStatus": "OK",
  "inputStatus": "NORMAL"
}
```

---

### Fields

| Field          | Type   | Description |
| -------------- | ------ | ----------- |
| batteryVoltage | number | ولتاژ باتری |
| inputVoltage   | number | ورودی       |
| batteryStatus  | string | وضعیت باتری |
| inputStatus    | string | وضعیت ورودی |

---

### Battery Status

| مقدار    | توضیح  |
| -------- | ------ |
| OK       | نرمال  |
| LOW      | ضعیف   |
| CRITICAL | بحرانی |

---
