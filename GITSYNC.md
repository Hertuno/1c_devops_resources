### Команды инициализации и включения выгрузки в формат EDT
```CMD
gitsync p init
gitsync p enable edtExport
gitsync p ls -a
```

### Команда для выгрузки хранилища расширения в формат EDT
```CMD
set GITSYNC_WORKDIR="директория выгрузки"            
set GITSYNC_WORKSPACE_LOCATION="директория с проектом EDT" 
set GITSYNC_STORAGE_PATH="путь к хранилищу"                
set GITSYNC_STORAGE_USER="пользователь хранилища"          
set GITSYNC_STORAGE_PASSWORD="пароль хранилища"            
set GITSYNC_EXTENSION="имя расширения"                     
set GITSYNC_DISABLE_AUTO_SRC=true & :: Не искать в репозитории каталог src

gitsync --ib-user "пользователь временной ИБ" --ib-pwd "пароль временной ИБ" --ib-connection /S"кластер"\"имя ИБ" sync --project-name "имя проекта" "путь к хранилищу" "директория выгрузки"
```

### Прочее
Для выгрузки при помощи свежих EDT (от 2024 версии) необходима версия плагина edtExport 1.4.0, её можно скачать из ветки разработки основного репозитория
[edtExport.os](https://github.com/oscript-library/gitsync-plugins/blob/d61feeaeaf88c72c73811f2065d3d8d540756fb5/src/%D0%9A%D0%BB%D0%B0%D1%81%D1%81%D1%8B/edtExport.os)
и заменить в AppData пользователя от которого работает gitsync 
```%appdata%\Local\gitsync\plugins\gitsync-plugins\src\Классы\```

В дирректории выгрузки нужно создать файл VERSION, с версией сборки хранилища, от которой будет происходить выгрузка (если указать 0, хранилище выгрузится полностью)
```HTML
<?xml version="1.0" encoding="UTF-8"?>
<VERSION>0</VERSION>
```
