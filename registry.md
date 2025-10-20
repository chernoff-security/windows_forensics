# Корневые ключи реестра:
| Корневой ключ       | Сокращение | Содержание                                                                                             |
| ------------------- | ---------- | ------------------------------------------------------------------------------------------------------ |
| HKEY_CLASSES_ROOT   | HKCR       | Типы файлов и их ассоциации                                                                            |
| HKEY_CURRENT_CONFIG | HKCC       | Информация о профиле оборудования, используемом локальным компьютером при запуске системы              |
| HKEY_CURRENT_USER   | HKCU       | Корень информации о конфигурации для пользователя, который находится в системе в данный момент         |
| HKEY_USERS          | HKU        | Все загруженные профили пользователей. Является подразделом HKCU                                       |
| HKEY_LOCAL_MACHINE  | HKLM       | Данные о системной шине, портах, контроллерах и других аппаратных компонентах, сведения о безопасности |
# Расположение кустов реестра и полезные файлы:
| Путь                                                              | Файл                            | Содержание файла                                                                   |
| ----------------------------------------------------------------- | ------------------------------- | ---------------------------------------------------------------------------------- |
| C:\\Windows\\System32\\Config                                     | DEFAULT                         | Данные HKEY_USERS\DEFAULT                                                          |
| C:\\Windows\\System32\\Config                                     | SAM (Security Accounts Manager) | Данные HKEY_LOCAL_MACHINE\SAM                                                      |
| C:\\Windows\\System32\\Config                                     | SECURITY                        | HKEY_LOCAL_MACHINE\Security                                                        |
| C:\\Windows\\System32\\Config                                     | SOFTWARE                        | HKEY_LOCAL_MACHINE\Software                                                        |
| C:\\Windows\\System32\\Config                                     | SYSTEM                          | HKEY_LOCAL_MACHINE\System                                                          |
| C:\\Windows\\System32\\Config                                     | *.LOG                           | Журнал изменений реестра                                                           |
| C:\\Users\\_пользователь_\\AppData<br>\\Local\\Microsoft\\Windows | NTUSER.DAT                      | Информация, которая при авторизации данного пользователя в системе попадает в HKCU |
# Полезные значения реестра:
###### **SYSTEM:**
| Информация                                                    | Расположение значения                                                                                              |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Имя компьютера                                                | CurrentControlSet\Control\ComputerName\ComputerName **или** ControlSet001\Control\ComputerName\ComputerName        |
| Часовой пояс                                                  | CurrentControlSet\Control\TimeZoneInformation                                                                      |
| Список сетевых интерфейсов                                    | CurrentControlSet\Services\Tcpip\Parameters\Interfaces\\*                                                          |
| Подключения устройств                                         | CurrentControlSet\Enum\USBSTOR, CurrentControlSet\Enum\USB,<br>ControlSet001\Enum\USBSTOR и ControlSet001\Enum\USB |
| Службы                                                        | CurrentControlSet\Services\\*                                                                                      |
| AppCompatCache / ShimCache запускаемые приложения             | CurrentControlSet\Control\Session Manager\AppCompatCache > AppCompatCache                                          |
| Бук­ва, наз­начен­ная сис­темой под­клю­чен­ному устрой­ству: | MountedDevices                                                                                                     |
| Название устройства                                           | Microsoft\Windows Portable Devices\Devices\\*\FriendlyName                                                         |
###### SOFTWARE:
| Информация                                                           | Расположение значения                                                                                                                      |
| -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Версия ОС                                                            | Microsoft\Windows NT\CurrentVersion                                                                                                        |
| Сети, к которым был подключен компьютер                              | Microsoft\Windows NT\CurrentVersion\NetworkList                                                                                            |
| Автозапуск приложений                                                | Microsoft\Windows\CurrentVersion\Run, Microsoft\Windows\CurrentVersion\RunOnce и<br>Microsoft\Windows\CurrentVersion\policies\Explorer\Run |
| Недавно открытые документы                                           | Microsoft\Office                                                                                                                           |
| Пользователи                                                         | Microsoft\Windows NT\CurrentVersion\ProfileList\\%SID%                                                                                     |
| Установленные антивирусы и их статус                                 | Microsoft\Security Center\Provider\Av\\*                                                                                                   |
| Установленные патчи и обновления                                     | Microsoft\Windows\CurrentVersion\Component Based Servicing\Packages\\*                                                                     |
| Время последнего входа в систему                                     | Microsoft\Windows\CurrentVersion\Authentication\LogonUI                                                                                    |
| Установленное ПО                                                     | Microsoft\Windows\CurrentVersion\Uninstall\\* и WOW6432Node\Microsoft\Windows\CurrentVersion\Uninstall\\*                                  |
| Планировщик заданий                                                  | Microsoft\Windows NT\CurrentVersion\Schedule\Taskcache\Tree\\* и Microsoft\Windows NT\CurrentVersion\Schedule\Taskcache\Tasks\\*           |
| Устройства, связанные с ними идентификаторы и история форматирований | Microsoft\Windows NT\CurrentVersion\EMDMgmt                                                                                                |
###### SAM:
| Информация                    | Расположение значения                                       |
| ----------------------------- | ----------------------------------------------------------- |
| Информация об учетных записях | Domains\Account\Users **(примечание: время в формате UTC)** |
###### NTUSER.DAT:
| Информация                                                               | Расположение значения                                                                             |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| Автозапуск приложений                                                    | Software\Microsoft\Windows\CurrentVersion\Run и Software\Microsoft\Windows\CurrentVersion\RunOnce |
| Недавно открытые файлы                                                   | Software\Microsoft\Windows\CurrentVersion\Explorer\RecentDocs                                     |
| Пользователи в группах                                                   | SOFTWARE\Microsoft\Windows\CurrentVersion\Group Policy\GroupMembership                            |
| UserAssist запускаемые приложение с GUI                                  | SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\UserAssist\*                                   |
| RunMRU (Most Recently Used) история команд в "Выполнить"                 | SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\RunMRU\*                                       |
| RecentApps Последние приложения, открытые через «Пуск» или Task Switcher | SOFTWARE\Microsoft\Windows\CurrentVersion\Search\RecentApps\*                                     |
| Удаленно подключенные диски                                              | SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\MountPoints2\\*                                |
# Дополнительная информация:
**Резервные копии кустов реестра:**
	C:\\Windows\\System32\\Config\\RegBack
**Информация о запускаемых приложениях:**
	C:\\Windows\\AppCompat\\Programs\\Amcache.hve
	C:\\Windows\\AppCompat\\Programs\\ShimCache.hve
	Данные хранятся в ключе реестра **CacheMainSdb**:
	`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\AppCompatCache`
	`HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Session Manager\AppCompatCache`
