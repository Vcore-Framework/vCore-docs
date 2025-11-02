---
description: Pengenalan lengkap tentang vCore Framework
---

# 📖 What is vCore?

## Overview

vCore adalah framework FiveM modern yang didesain dengan fokus pada **performa**, **modularitas**, dan **kemudahan penggunaan**. Framework ini menyediakan foundation yang solid untuk membangun roleplay server berkualitas tinggi.

{% hint style="success" %}
vCore dibangun dengan best practices dan modern coding standards untuk memastikan server Anda berjalan dengan optimal.
{% endhint %}

## 🎯 Philosophy

vCore Framework dibangun dengan 4 prinsip utama:

### 1. Clean Architecture
```lua
-- Struktur kode yang jelas dan mudah dipahami
vCore.Functions.CreatePlayer(source, identifier, function(player)
    player.setJob('police', 0)
    player.addMoney('bank', 5000)
end)
```

Setiap komponen memiliki tanggung jawab yang jelas dan terpisah, membuat kode mudah dimaintain dan dikembangkan.

### 2. Performance First

* **Optimized loops** - Tidak ada unnecessary loops
* **Event-driven** - Efficient event handling system
* **Database pooling** - Connection pooling untuk performa database
* **Resource monitoring** - Built-in performance monitoring

### 3. Developer Experience
```lua
-- API yang intuitif dan mudah digunakan
local xPlayer = vCore.GetPlayer(source)

if xPlayer.hasJob('police') then
    xPlayer.showNotification('Welcome, Officer!', 'success')
end
```

API dirancang untuk mudah dipahami dan digunakan, bahkan untuk developer pemula.

### 4. Extensibility
```lua
-- Mudah untuk extend functionality
vCore.RegisterCallback('vcore:getCustomData', function(source, cb)
    -- Your custom logic here
    cb(customData)
end)
```

## 🏗️ Architecture

vCore menggunakan **modular monolithic architecture** yang memisahkan concerns dengan jelas:
