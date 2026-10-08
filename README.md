<h1 align="center">ChatGPT для Windows</h1>
<p align="center">Установка без Microsoft Store</p>

<p align="center">
  <a href="#install">Установка</a> ·
  <a href="#chats">Чаты</a> ·
  <a href="#problems">Проблемы</a>
</p>

Если Microsoft Store не работает, ChatGPT можно поставить вручную. Для этого OpenAI публикует MSIX-пакет и файл лицензии. Способ описан в [документации][deployment].

<a id="install"></a>

## Установка

### 1. Скачай два файла

Сначала выбери приложение под свой компьютер:

| Windows | Файл |
| :--- | :--- |
| 64-разрядная Windows на Intel / AMD | [ChatGPT-x64.msix][download-x64] |
| Windows ARM64, например на ноутбуке со Snapdragon | [ChatGPT-arm64.msix][download-arm64] |

Ещё нужен [ChatGPT-License.xml][download-license]. Если он открылся в браузере как текст, нажми **Ctrl + S** и сохрани с этим именем. Проверь, что в конце не добавилось `.txt` или `.html`.

<details>
<summary>Как выбрать версию</summary>

В параметрах Windows открой **Система → О системе → Тип системы**. Там указаны разрядность Windows и архитектура процессора. Для 32-разрядной Windows эти пакеты не подойдут, даже если процессор поддерживает x64.

</details>

### 2. Подготовь папку

Создай `C:\ChatGPT-Install` и положи туда оба файла. Приложение переименуй в `ChatGPT.msix`, имя лицензии оставь как есть:

```text
C:\ChatGPT-Install\ChatGPT.msix
C:\ChatGPT-Install\ChatGPT-License.xml
```

При переименовании включи отображение расширений в Проводнике, чтобы случайно не получить `ChatGPT.msix.msix`.

### 3. Установи приложение

В «Пуске» найди **Windows PowerShell**, нажми на него правой кнопкой и выбери **«Запуск от имени администратора»**. Вставь команду целиком и нажми Enter:

```powershell
Add-AppxProvisionedPackage -Online -PackagePath "C:\ChatGPT-Install\ChatGPT.msix" -LicensePath "C:\ChatGPT-Install\ChatGPT-License.xml" -Regions all
```

После установки открой ChatGPT и войди в аккаунт, которым пользуешься на сайте. Если приложения нет в «Пуске», выйди из учётной записи Windows и войди снова.

Интернет для работы ChatGPT всё равно нужен. Из локальных файлов устанавливается только приложение.

<a id="chats"></a>

## Чаты из браузера

Вверху слева открой меню **«Codex ▾»** и выбери **ChatGPT**. У этих разделов разные списки чатов:

| Раздел | Что в нём находится |
| :--- | :--- |
| ChatGPT | Обычные чаты из браузера и телефона, а также разговоры Work |
| Codex | Чаты Codex и проекты для разработки |

[Подробнее о разделах приложения][use-chatgpt].

Если чатов нет, проверь аккаунт, рабочее пространство и архив. У старых локальных задач Work есть [отдельные условия синхронизации][troubleshooting].

<a id="problems"></a>

## Если что-то не работает

### «Скачивание 0%»

По этой надписи не видно, что именно загружается. Если процент долго не меняется:

1. Нажми на индикатор и посмотри, открываются ли подробности.
2. Полностью закрой приложение и запусти заново.
3. Если пользуешься VPN, проверь, работает ли он для всего компьютера. Расширения в браузере обычно недостаточно. Можно попробовать другой сервер.

Если не помогло, сохрани текст ошибки и версии приложения и Windows.

Если зависло именно обновление приложения, проверь доступ к `persistent.oaistatic.com`. Этот адрес указан в [инструкции OpenAI][deployment].

### Ошибки установки

| Ошибка | Что сделать |
| :--- | :--- |
| Файл не найден | Проверь папку `C:\ChatGPT-Install` и имена файлов. Они должны совпадать с командой |
| `0x80073D28` | Запусти Windows PowerShell от имени администратора. Эта ошибка означает, что установке не хватает прав |
| Пакет несовместим с Windows | Проверь архитектуру пакета и требования к Windows в тексте ошибки |
| Установка запрещена политикой | Посмотри, какой запрет указан. На рабочем или учебном компьютере это нужно решать с администратором |

[Ошибки установки в документации][deployment].

<details>
<summary>Установка через winget</summary>

В документации есть и такая команда:

```powershell
winget install --id 9PLM9XGG6VKS -s msstore
```

Она обращается к Microsoft Store. Если его сервисы недоступны, используй способ с MSIX выше. [Источник команды][windows-app].

</details>

<details>
<summary>Обновления</summary>

Обычно приложение обновляется само. В рабочем пространстве настройки обновлений может задавать администратор. [Документация][updates].

</details>

## Документация

- [Установка на Windows][deployment]
- [Приложение ChatGPT для Windows][windows-app]
- [Первый запуск][quickstart]
- [ChatGPT и Codex][use-chatgpt]
- [Проблемы с чатами][troubleshooting]
- [Обновления][updates]

Обновлено: 8 октября 2026.

[download-x64]: https://persistent.oaistatic.com/codex-app-prod/ChatGPT-x64.msix
[download-arm64]: https://persistent.oaistatic.com/codex-app-prod/ChatGPT-arm64.msix
[download-license]: https://persistent.oaistatic.com/codex-app-prod/ChatGPT-License.xml
[deployment]: https://learn.chatgpt.com/docs/enterprise/windows-deployment
[windows-app]: https://learn.chatgpt.com/docs/windows/windows-app
[quickstart]: https://learn.chatgpt.com/docs/quickstart
[use-chatgpt]: https://learn.chatgpt.com/docs/use-chatgpt
[troubleshooting]: https://learn.chatgpt.com/docs/reference/troubleshooting
[updates]: https://learn.chatgpt.com/docs/enterprise/manage-app-updates
