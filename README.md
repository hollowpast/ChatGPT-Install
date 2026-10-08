<h1 align="center">ChatGPT для Windows</h1>
<p align="center">Установка без Microsoft Store</p>

## 1. Скачай два файла

- **[Приложение ChatGPT](https://persistent.oaistatic.com/codex-app-prod/ChatGPT-x64.msix)** — для компьютеров с Intel или AMD.
- **[Файл лицензии](https://persistent.oaistatic.com/codex-app-prod/ChatGPT-License.xml)** — тоже нужен для установки.

На компьютере со Snapdragon вместо первого файла скачай **[версию ARM64](https://persistent.oaistatic.com/codex-app-prod/ChatGPT-arm64.msix)**.

Если лицензия открылась как текст, нажми **Ctrl + S** и сохрани её как `ChatGPT-License.xml`.

## 2. Положи файлы в одну папку

Открой **«Этот компьютер» → «Диск C:»**. Создай папку **ChatGPT** и перенеси туда оба файла.

Из имени установщика удали только `-x64` или `-arm64`. Файл лицензии не переименовывай. Получится:

```text
C:\ChatGPT\ChatGPT.msix
C:\ChatGPT\ChatGPT-License.xml
```

## 3. Установи приложение

Нажми **«Пуск»** и напиши `PowerShell`. У **Windows PowerShell** выбери **«Запуск от имени администратора»**, затем **«Да»**.

Скопируй всю команду ниже, вставь в открывшееся окно и нажми **Enter**:

```powershell
Add-AppxProvisionedPackage -Online -PackagePath "C:\ChatGPT\ChatGPT.msix" -LicensePath "C:\ChatGPT\ChatGPT-License.xml" -Regions all
```

Дождись завершения установки. Сохрани открытые документы и перезагрузи компьютер.

Открой **ChatGPT** через **«Пуск»** и войди в свой аккаунт.

---

[Официальная инструкция OpenAI](https://learn.chatgpt.com/docs/enterprise/windows-deployment)
