# AirdropManager - Продвинутая система аирдропов для Unturned

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![RocketMod](https://img.shields.io/badge/RocketMod-4.9.3+-green.svg)
![Unturned](https://img.shields.io/badge/Unturned-3.23.x+-orange.svg)

**AirdropManager** - это мощный плагин для серверов Unturned на платформе RocketMod, который полностью заменяет стандартную систему аирдропов, предоставляя гибкие настройки лута, множественные типы аирдропов и информативные уведомления.

## 🚀 Основные возможности

- ✅ **Полная замена ванильной системы** - отключает стандартные аирдропы и заменяет их кастомными
- ✅ **Множественные типы аирдропов** - Military, Medical, Supply и любые другие по вашему желанию
- ✅ **Гибкая настройка лута** - индивидуальные шансы выпадения для каждого предмета
- ✅ **Автоматические уведомления** - игроки видят когда и куда летит аирдроп
- ✅ **Определение локаций** - аирдропы падают возле известных мест (Alberton, Seattle и т.д.)
- ✅ **Звуковые эффекты** - настраиваемые звуки при прилёте и приземлении
- ✅ **Команды администратора** - ручной вызов аирдропов и управление системой
- ✅ **Система весов** - контроль частоты появления разных типов аирдропов

## ⚙️ Конфигурация

После первого запуска в папке `Rocket/Plugins/` появится файл конфигурации:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Configuration>
    <!-- Основные настройки -->
    <EnableCustomAirdrops>true</EnableCustomAirdrops>
    <DisableVanillaAirdrops>true</DisableVanillaAirdrops>
    
    <!-- Уведомления -->
    <ShowAnnouncements>true</ShowAnnouncements>
    <PlaySounds>true</PlaySounds>
    <AnnounceIncomingSound>0</AnnounceIncomingSound>
    <AnnounceLandedSound>0</AnnounceLandedSound>
    
    <!-- Частота появления (в секундах) -->
    <MinAirdropInterval>900</MinAirdropInterval>   <!-- 15 минут -->
    <MaxAirdropInterval>1800</MaxAirdropInterval>  <!-- 30 минут -->
    
    <!-- Параметры полёта -->
    <AirdropSpeed>32</AirdropSpeed>
    <AirdropHeight>450</AirdropHeight>
    
    <!-- Типы аирдропов -->
    <AirdropTypes>
        <AirdropType>
            <Name>Military</Name>
            <Weight>25</Weight>
            <ContainerID>1372</ContainerID>
            <Items>
                <Item>
                    <ItemID>363</ItemID>      <!-- Maplestrike -->
                    <MinAmount>1</MinAmount>
                    <MaxAmount>1</MaxAmount>
                    <Chance>80</Chance>
                </Item>
                <Item>
                    <ItemID>119</ItemID>      <!-- Military Magazine -->
                    <MinAmount>2</MinAmount>
                    <MaxAmount>4</MaxAmount>
                    <Chance>70</Chance>
                </Item>
            </Items>
        </AirdropType>
        
        <AirdropType>
            <Name>Medical</Name>
            <Weight>30</Weight>
            <ContainerID>1372</ContainerID>
            <Items>
                <Item>
                    <ItemID>15</ItemID>       <!-- Bandage -->
                    <MinAmount>3</MinAmount>
                    <MaxAmount>6</MaxAmount>
                    <Chance>100</Chance>
                </Item>
                <Item>
                    <ItemID>14</ItemID>       <!-- Morphine -->
                    <MinAmount>2</MinAmount>
                    <MaxAmount>4</MaxAmount>
                    <Chance>80</Chance>
                </Item>
            </Items>
        </AirdropType>
    </AirdropTypes>
</Configuration>
```

### Описание настроек

| Параметр | Описание | Значение по умолчанию |
|----------|----------|----------------------|
| `EnableCustomAirdrops` | Включить кастомные аирдропы | `true` |
| `DisableVanillaAirdrops` | Отключить стандартные аирдропы | `true` |
| `ShowAnnouncements` | Показывать уведомления в чате | `true` |
| `PlaySounds` | Воспроизводить звуки | `true` |
| `MinAirdropInterval` | Минимальный интервал между аирдропами (сек) | `900` |
| `MaxAirdropInterval` | Максимальный интервал между аирдропами (сек) | `1800` |
| `AirdropSpeed` | Скорость полёта аирдропа | `32` |
| `AirdropHeight` | Высота появления аирдропа | `450` |

### Настройка типов аирдропов

Каждый тип аирдропа содержит:

- **Name** - название типа (отображается в уведомлениях)
- **Weight** - вес для случайного выбора (чем больше, тем чаще)
- **ContainerID** - ID контейнера для лута
- **Items** - список предметов с настройками:
  - **ItemID** - ID предмета
  - **MinAmount/MaxAmount** - минимальное/максимальное количество
  - **Chance** - шанс выпадения (0-100%)

## 🎮 Команды

Все команды требуют права `airdrop.admin`.

### Основные команды

| Команда | Описание | Пример |
|---------|----------|--------|
| `/airdrop spawn <тип>` | Вызвать аирдроп к себе | `/airdrop spawn military` |
| `/airdrop spawn <тип> <локация>` | Вызвать аирдроп к локации | `/airdrop spawn medical alberton` |
| `/airdrop reload` | Перезагрузить конфигурацию | `/airdrop reload` |
| `/airdrop list` | Показать список локаций | `/airdrop list` |
| `/airdrop types` | Показать типы аирдропов | `/airdrop types` |

### Альтернативная команда
Можно использовать сокращение `/ad` вместо `/airdrop`.

## 📝 Примеры использования

### Вызов аирдропа
```
/airdrop spawn military
> ✅ Аирдроп 'Military' вызван к рядом с Alberton!
```

### Уведомления для игроков
```
🛩️ Военный аирдроп типа 'Military' направляется к Alberton!
📦 Аирдроп 'Medical' приземлился рядом с Seattle!
```

### Добавление нового типа аирдропа

Добавьте в конфигурацию:

```xml
<AirdropType>
    <Name>Rare</Name>
    <Weight>5</Weight>
    <ContainerID>1372</ContainerID>
    <Items>
        <Item>
            <ItemID>1394</ItemID>  <!-- Grizzly -->
            <MinAmount>1</MinAmount>
            <MaxAmount>1</MaxAmount>
            <Chance>50</Chance>
        </Item>
        <Item>
            <ItemID>1395</ItemID>  <!-- Grizzly Magazine -->
            <MinAmount>1</MinAmount>
            <MaxAmount>3</MaxAmount>
            <Chance>80</Chance>
        </Item>
    </Items>
</AirdropType>
```

## 🔧 Права доступа

Добавьте в `Permissions.config.xml`:

```xml
<Permission Cooldown="0">airdrop.admin</Permission>
```

Или выдайте права конкретному игроку:
```
/p add <игрок> airdrop.admin
```

## ❓ Часто задаваемые вопросы

### В: Можно ли использовать плагин с ванильными аирдропами?
**О:** Да, но рекомендуется отключать ванильные (`DisableVanillaAirdrops = true`) для лучшего контроля.

### В: Как изменить частоту аирдропов?
**О:** Настройте `MinAirdropInterval` и `MaxAirdropInterval` в секундах. Например, для аирдропов каждые 5-10 минут: Min=300, Max=600.

### В: Почему аирдроп не содержит лут?
**О:** Проверьте правильность ID предметов и контейнера в конфигурации. Убедитесь, что шансы выпадения больше 0.

### В: Как добавить звуки?
**О:** Найдите ID звуковых эффектов и укажите их в `AnnounceIncomingSound` и `AnnounceLandedSound`.

### В: Аирдропы не появляются автоматически
**О:** Убедитесь что:
- `EnableCustomAirdrops = true`
- На сервере есть игроки
- Интервалы настроены правильно
- Проверьте логи на ошибки

## 🐛 Устранение неполадок

### Плагин не загружается
1. Проверьте версию RocketMod (нужна 4.9.3+)
2. Убедитесь что файл `0Harmony.dll` есть в папке Rocket
3. Проверьте логи сервера на ошибки

### Ошибки в конфигурации
1. Убедитесь что XML-файл корректен
2. Проверьте ID предметов и контейнеров
3. Используйте `/airdrop reload` после изменений

### Аирдропы пустые
1. Проверьте правильность ItemID
2. Убедитесь что ContainerID существует
3. Проверьте шансы выпадения (Chance)
4. 
---

**Разработано для сообщества Unturned с ❤️**
