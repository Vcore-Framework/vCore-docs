### Layers Explanation

#### **Server side**
Menangani semua logic server-side:
* Player management
* Database operations
* Permission checks
* Event handling

#### **Client side**
Menangani semua interaksi dengan player:
* UI rendering
* Input handling
* Visual effects
* Client-side validation

#### **Shared side**
Code yang digunakan di client dan server:
* Configuration
* Locale/translations
* Utility functions
* Constants

#### 🗄️ **Database Layer**
Abstraction layer untuk database operations:
* Query builder
* Connection pooling
* Transaction support
* Migration system

### Player System
Comprehensive player management dengan support untuk:
* Multiple characters per account
* Character identity (name, DOB, gender)
* Job system dengan grades
* Money management (cash, bank, black money)
* Inventory system
* Metadata storage

### Event System
Event-driven architecture yang efficient:
```lua
-- Register event
RegisterNetEvent('vcore:server:doSomething')
AddEventHandler('vcore:server:doSomething', function(data)
    -- Handle event
end)

-- Trigger event
TriggerServerEvent('vcore:server:doSomething', {key = 'value'})
```

### Callback System
Synchronous-like async operations:
```lua
-- Server callback
vCore.RegisterCallback('vcore:getData', function(source, cb)
    cb({data = 'value'})
end)

-- Client usage
vCore.TriggerCallback('vcore:getData', function(result)
    print(result.data)
end)
```

### Database Integration
Built-in MySQL/MariaDB support dengan:
* Prepared statements
* Connection pooling
* Transaction support
* Query builder

## Design Patterns

vCore mengimplementasikan several design patterns:

### Singleton Pattern
```lua
-- vCore instance adalah singleton
local vCore = exports['vCore']:getSharedObject()
```

### Factory Pattern
```lua
-- Player objects dibuat dengan factory pattern
vCore.Functions.CreatePlayer(source, identifier)
```

### Observer Pattern
```lua
-- Event system menggunakan observer pattern
AddEventHandler('vcore:playerLoaded', function(player)
    -- React to player loaded
end)
```

## Security

vCore Framework memiliki beberapa security features:

### Server-side Validation
Semua critical operations divalidasi di server:
```lua
-- ❌ BAD: Client can modify directly
TriggerServerEvent('vcore:giveMoney', 999999)

-- ✅ GOOD: Server validates
RegisterNetEvent('vcore:requestReward')
AddEventHandler('vcore:requestReward', function()
    local xPlayer = vCore.GetPlayer(source)
    if xPlayer.hasPermission('admin') then
        xPlayer.addMoney('bank', 1000)
    end
end)
```

### SQL Injection Prevention
Menggunakan prepared statements:
```lua
-- ✅ SAFE: Parameterized query
vCore.Database.Execute('UPDATE users SET money = ? WHERE identifier = ?', {
    money, identifier
})
```

### Permission System
Role-based access control:
```lua
vCore.RegisterCommand('admin', 'admin', function(xPlayer, args)
    -- Only admin can use
end)
```

## Who Should Use vCore?

vCore cocok untuk:

**Server owners** yang ingin framework modern dan performance
**Teams** yang butuh framework mudah di-maintain  
**Beginners** yang ingin belajar framework dengan dokumentasi lengkap  

## Next Steps

{% content-ref url="features.md" %}
[features.md](features.md)
{% endcontent-ref %}

{% content-ref url="../installation/" %}
[installation](../installation/)
{% endcontent-ref %}
