<div align="center">

# ⚡ FunPulse (FunPay Tools Ecosystem)

**Автоматизация торговли на FunPay: расширение для ПК и автономный APK для Android**

[![Platform](https://img.shields.io/badge/Platform-Chrome_Extension_%7C_Android_APK-10b981?style=for-the-badge)](https://github.com/yrybacode/funpay-tools-mobile)
[![License](https://img.shields.io/badge/License-MIT-06b6d4?style=for-the-badge)](LICENSE)
[![GitHub Actions](https://img.shields.io/badge/Build-Passing-22c55e?style=for-the-badge&logo=githubactions&logoColor=white)](https://github.com/yrybacode/funpay-tools-mobile/actions)

<p align="center">
  <a href="#-архитектура-решения">Архитектура</a> •
  <a href="#-возможности">Возможности</a> •
  <a href="#-установка-на-пк-расширение">Установка на ПК</a> •
  <a href="#-установка-на-android-apk">Установка на Android</a> •
  <a href="#-безопасность">Безопасность</a>
</p>

---

</div>

## 📌 Архитектура экосистемы

FunPulse разделен на два взаимодополняющих формата:

1. **💻 На ПК (Браузерное расширение Manifest V3):**
   * Работает в **Google Chrome, Яндекс.Браузере, Firefox, Opera, Edge**.
   * Не требует установки Python, сторонних программ или ручного поиска cookie: встраивается прямо в открытую вкладку FunPay и подхватывает сессию автоматически.
2. **📱 На Android (Нативное приложение .APK):**
   * Собрано на **Kotlin + Jetpack Compose**.
   * Работает автономно 24/7 через системную фоновую службу (`Foreground Service`), позволяя автоматизировать торговлю без включенного компьютера.

---

## 🚀 Возможности

| Модуль | ПК (Расширение) | Android (.APK) |
| :--- | :---: | :---: |
| ⚡ **Мгновенная автовыдача** | Вкладка браузера | Фоновый процесс |
| 🔄 **Автоподнятие лотов раз в 4ч** | Фоновый Service Worker | WorkManager |
| 🟢 **Вечный Online** | Heartbeat через браузер | Foreground Service |
| 💬 **Автоответчик покупателям** | Да | Да |
| 🔔 **Уведомления о заказах** | Системные уведомления браузера + звук | Push-уведомления со шторки Android |
| 🔒 **Авторизация** | Автоматически по текущей сессии | Защищенный Keystore (AES-256) |

---

## 💻 Установка на ПК (Браузерное расширение)

1. Скачайте архив с расширением `funpulse-extension.zip` из раздела [Releases](https://github.com/yrybacode/funpay-tools-mobile/releases) и распакуйте в отдельную папку.
2. Откройте в браузере страницу расширений:
   * **Chrome / Яндекс:** `chrome://extensions/`
   * **Firefox:** `about:debugging#/runtime/this-firefox`
   * **Edge:** `edge://extensions/`
3. В правом верхнем углу включите тумблер **«Режим разработчика»** (Developer mode).
4. Нажмите кнопку **«Загрузить распакованное расширение»** (Load unpacked) и укажите распакованную папку.
5. Откройте сайт FunPay — в правом верхнем углу сайта появится панель управления FunPulse.

---

## 📱 Установка на Android (APK-файл)

1. Перейдите во вкладку [**Actions**](https://github.com/yrybacode/funpay-tools-mobile/actions) репозитория.
2. Откройте последнюю успешную сборку (с зеленой галочкой).
3. В блоке **Artifacts** скачайте архив `FunPay-Tools-Debug-APK`.
4. Распакуйте архив и установите полученный `.apk` на свой смартфон.
5. Введите `golden_key` и включите необходимые модули автовыдачи и поднятия лотов.

---

## 🛡️ Безопасность

* **Без передачи токенов:** Все данные хранятся исключительно локально (в `chrome.storage.local` браузера или в зашифрованном `Android Keystore`).
* **Прямые запросы:** Запросы отправляются напрямую на адреса `funpay.com` без промежуточных серверов или аналитики разработчика.

---

## 📄 Лицензия

Проект распространяется под свободной лицензией [MIT](LICENSE).
