# Задание 1. Разделить проект Mesto на несколько микрофронтендов
## Уровень 1. Проектирование

В целом, и Module Federation И Single SPA подходят для реализации микрофронтендного решения. Однако у каждого из подходов 
есть свои минусы:

#### Минусы Single SPA
1. Возможность реализации с использованием нескольких фреймворков может оказаться минусом в случае, если разработчиков 
в компании не так много. Может получиться так, что не будет возможности, в случае, например, увольнения, просто произвести 
ротацию и перевести разработчика с другого микрофронтенда.

#### Минусы Module Federation
1. Нет явного инструмента для обработки случая недоступности микрофронта
2. Не поддерживает версионирование, то есть у микрофронта всегда должна быть актуальная версия.

В рамках учебного проекта (нет необходимости в высокой производительности и использования преимуществ подхода с 
разработкой на нескольких фреймворках) имеет смысл использовать **Module Federation**. Для реального высоконагруженного 
проекта с индивидуальными требованиями для разного функционала и большой командой разработки я бы предпочел использовать 
**Single SPA**.

## Уровень 2. Планирование изменений

Проект разделен на 4 микрофронтенда:
1. **auth-microfrontend** - микрофронтенд, отвечающий за авторизацию и регистрацию пользователей
2. **host** - основное приложение, загружающее другие микрофронтенды
3. **place-microfrontend** - микрофронтенд, отвечающий за работу с местами (отображение, добавление)
4. **profile-microfrontend** - микрофронтенд, отвечающий за работу с профилем пользователей

+выделен модуль с общими компонентами - **common**

Структура проекта:
```
microfrontend
    auth-microfrontend
       src
            blocks
                auth-form
                login
            components
                Login.js
                Register.js
            context
                CurrentUserContext.js
            utils
                auth.js
    common
        components
            PopupWithForm.js
    host
        src
            blocks
                content
                footer
                header
                page
                popup
            components
                App.js
                Footer.js
                Header.js
                InfoTooltip.js
                Main.js
                ProtectedRoute.js
            images
            utils
            vendor
                fonts
            index.js
            index.css
    place-microfrontend
        src
            blocks
                card
                places
            components
                AddPlacePopup.js
                Card.js
                ImagePopup.js
            images
    profile-microfrontend
        src
            blocks
                profile
            components
                EditAvatarPopup.js
                EditProfilePopup.js
            images
```

# Задание 2. Декомпозировать веб-приложения на Django на микросервисы
Решение задания в файле [Задание_2](./Задание_2.drawio)