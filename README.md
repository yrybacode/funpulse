<div align="center">

# ⚡ FunPulse (FunPay Tools Mobile)

**Полная и автономная автоматизация торговли на FunPay прямо со смартфона**

[![Android](https://img.shields.io/badge/Platform-Android_8.0%2B-10b981?style=for-the-badge&logo=android&logoColor=white)](https://github.com/yrybacode/funpay-tools-mobile)
[![Kotlin](https://img.shields.io/badge/Kotlin-1.9.24-6366f1?style=for-the-badge&logo=kotlin&logoColor=white)](https://kotlinlang.org/)
[![License](https://img.shields.io/badge/License-MIT-06b6d4?style=for-the-badge)](LICENSE)
[![GitHub Actions](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-22c55e?style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/yrybacode/funpay-tools-mobile/actions)

<p align="center">
  <a href="#-возможности">Возможности</a> •
  <a href="#-стек-технологий">Стек технологий</a> •
  <a href="#-установка-и-запуск">Установка</a> •
  <a href="#-безопасность">Безопасность</a> •
  <a href="#-сборка-из-исходников">Сборка</a> •
  <a href="#-дисклеймер">Дисклеймер</a>
</p>

---

</div>

## 📌 О проекте

**FunPulse** — это нативное мобильное приложение для Android с открытым исходным кодом, предназначенное для продавцов площадки FunPay. 

Приложение не требует постоянно включенного ПК или аренды VDS/VPS: вся автоматизация (поднятие лотов, моментальная доставка товаров и поддержание статуса онлайн) выполняется **локально в фоновой службе смартфона** даже при заблокированном экране.

---

## 🚀 Возможности

| Модуль | Описание |
| :--- | :--- |
| ⚡ **Мгновенная автовыдача** | Доставка ключей, аккаунтов или ссылок покупателю в чат за 0.4–0.6 сек. сразу после подтверждения оплаты. |
| 🔄 **Автоподнятие лотов** | Автоматический подъем всех активных категорий каждые 4 часа со случайным смещением таймера для естественной имитации человека. |
| 🟢 **Вечный Online** | Периодическая фоновая отправка heartbeat-запросов для удержания статуса «В сети». |
| 💬 **Автоответчик и чат** | Приветствие при создании заказа и автоматические ответы на частые вопросы по ключевым словам. |
| 🔋 **Автономная работа 24/7** | Энергоэффективный сервис (`ForegroundService` + `WorkManager`), не выгружаемый оптимизаторами батареи Android. |
| 📊 **Локальный аудит** | Вся история сделок, логов и ошибок сохраняется локально в SQLite-базе данных (Room). |

---

## 🛡️ Безопасность и хранение данных

* **Аппаратное шифрование:** Токен сессии (`golden_key`) хранится локально с использованием `EncryptedSharedPreferences` и ключей в защищенном модуле **Android Keystore** (алгоритм AES-256-GCM).
* **Никаких сторонних серверов:** Все сетевые запросы отправляются напрямую между вашим смартфоном и серверами FunPay. Никаких прокси-серверов разработчика, метрик или скрытого сбора аналитики.

---

## 🛠️ Стек технологий

* **Язык:** Kotlin 1.9.24
* **UI-фреймворк:** Jetpack Compose + Material 3 (адаптивная темная тема)
* **Архитектура:** Clean Architecture + MVVM + StateFlow / Coroutines
* **База данных:** Room 2.6.1 + Kapt
* **Фоновые процессы:** Android Foreground Service + WorkManager
* **Сетевой слой:** OkHttp 4.12.0 + JSoup 1.18.1 (парсинг ответов)
* **Криптография:** AndroidX Security Crypto (AES-256)
* **Сборка:** Gradle 8.7 + GitHub Actions CI

---

## 📥 Установка и запуск

### Вариант 1. Скачать готовый APK через GitHub Actions

1. Перейдите во вкладку [**Actions**](https://github.com/yrybacode/funpay-tools-mobile/actions) репозитория.
2. Откройте последнюю успешную сборку (с зеленой галочкой).
3. В самом низу в блоке **Artifacts** скачайте архив `FunPay-Tools-Debug-APK`.
4. Распакуйте архив и установите `.apk` на свой смартфон (разрешив установку из неизвестных источников).

### Настройка в приложении:
1. Запустите FunPulse на смартфоне.
2. Вставьте свой `golden_key` (токен cookie из браузера) в разделе авторизации.
3. Включите нужные тумблеры: **Автовыдача**, **Автоподнятие лотов**, **Вечный онлайн**.
4. Разрешите приложению работу в фоновом режиме без оптимизации аккумулятора.

---

## 🔨 Сборка из исходников

### Через GitHub Actions (рекомендуется)
Каждый коммит в ветку `main` автоматически триггерит сборку свежего `.apk` через файл `.github/workflows/build.yml`. Также сборку можно запустить вручную через кнопку `Run workflow`.

### Локальная сборка через Android Studio / Терминал
```bash
# Клонирование репозитория
git clone [https://github.com/yrybacode/funpay-tools-mobile.git](https://github.com/yrybacode/funpay-tools-mobile.git)
cd funpay-tools-mobile

# Сборка Debug APK
./gradlew assembleDebug

# Готовый файл появится по пути:
# app/build/outputs/apk/debug/app-debug.apk
