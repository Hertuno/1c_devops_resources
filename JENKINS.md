# Различная информация по работе с jenkins

## Полезные Groovy Scripts

### Список информационных баз из mssql в список выбора для параметризированной сборки с отбором по имени начинающимся на "test"
```Groovy
def sqlCmd = ["sqlcmd","-S","mssql сервер","-U","пользователь","-P","пароль","-Q","SELECT name FROM sys.databases"].execute()
def result = sqlCmd.text
def params = result.split("\n")
def paramList = []
params.eachWithIndex { param, index ->
  if (index > 1 && index < params.size() - 2) {
    def paramName = param.trim()
    if (paramName.startsWith("test")) {
      paramList.add(paramName)
    }
  }
}
return paramList
```

### Список файлов директории в список выбора для параметризированной сборки
```Groovy
import groovy.io.FileType 

def fileList = []

def dir = new File("путь к директории")
dir.eachFileRecurse (FileType.FILES) { file ->
  fileList << file.name
}
return fileList
```

