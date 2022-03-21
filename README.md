# Глобальные данные
Реализации паттернов доступа к глобальным данным.

> Проверено на Unity 2020.3 (не зависит от нее) и содержит asmdef-описания для компиляции в виде отдельных сборок и уменьшения времени рекомпиляции основного проекта.

# Содержание
* [Социальные ресурсы](#socials)
* [Установка](#installation)
    * [В виде unity-модуля](#as-unity-module)
    * [В виде исходников](#as-source)
* [Классы](#classes)
    * [Service](#service)
* [Лицензия](#license)

# Социальные ресурсы
[![discord](https://img.shields.io/discord/404358247621853185.svg?label=enter%20to%20discord%20server&style=for-the-badge&logo=discord)](https://discord.gg/5GZVde6)

# Установка

## В виде unity-модуля
Поддерживается установка в виде unity-модуля через git-ссылку в PackageManager или прямое редактирование `Packages/manifest.json`:
```
"com.leopotam.globals": "https://github.com/Leopotam/globals.git",
```
По умолчанию используется последняя релизная версия. Если требуется версия "в разработке" с актуальными изменениями - следует переключиться на ветку `develop`:
```
"com.leopotam.globals": "https://github.com/Leopotam/globals.git#develop",
```

## В виде исходников
Код так же может быть склонирован или получен в виде архива со страницы релизов.

# Классы

## Service
Реализация паттерна `сервис-локатор`.

### Обычное применение
```csharp
class PlayerSession {
    public int Rank;
}

// Инициализация экземпляра.
Service<PlayerSession>.Set (new PlayerSession ());
// ...
// Запрос экземпляра.
Service<PlayerSession>.Get ().Rank = 10;
// ...
// Очистка.
Service<PlayerSession>.Set (null);
```

### Применение с автоматическим созданием экземпляра
```csharp
class PlayerSession {
    public int Rank;
}

// Запрос экземпляра. Если не существует - будет создан посредством вызова конструктора по умолчанию.
Service<PlayerSession>.Get(true).Rank = 10;
// ...
// Очистка.
Service<PlayerSession>.Set (null);
```

# Лицензия
Фреймворк выпускается под двумя лицензиями, [подробности тут](./LICENSE.md).

В случаях лицензирования по условиям MIT-Red не стоит расчитывать на
персональные консультации или какие-либо гарантии.