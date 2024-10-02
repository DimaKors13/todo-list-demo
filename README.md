# To-do list
## Список дел

To-do list это веб-приложение для ведения, мониторинга списка задач.

## Функции

- Ввод задач для выполнения
- Возможность указания наименования, комментария, крайнего срока выполнения задачи
- Возможность установки интервалов повторения задач

## Технологии

- [log/slog] - slog логгер
- [chi] - роутер http-сервера
- [SQLite] - база данных
- [testify] - модульное тестирование

## Реализация задач повышенной сложности

В качестве задачи повышенной сложности реализовано создание Docker образа для использования на Linux.

## Инструкция по запуску приложения и настройка

Для локального запуска приложения на хосте с ОС Windows следует выполнить следующую команду из корневой директории приложения ".../todo-list/" :
```sh
go build -o cmd/todo_app.exe cmd/main.go
```

Для запуска приложения в Docker контейнере на базе Ubuntu следует выполнить команду из корневой директории приложения ".../todo-list/":
```ps1
docker build -t todo_app:v1 .
docker run -it --rm -p 7540:7540 -v $PWD/database:/todo-list/database todo_app:v1
```
После запуска приложения вы можете получить доступ к клиентской части приложения по адресу "http://localhost:7540".

## Инструкция по запуску тестов
Необходимо установить следующие настрйоки тестирования в файле tests/settings.go:
```go
var Port = 7540
var DBFile = "../database/scheduler.db"
var FullNextDate = false
var Search = false
var Token = ``
```

   [log/slog]: <https://pkg.go.dev/log/slog@go1.23.1>
   [chi]: <https://github.com/go-chi/chi>
   [sqlite]: <https://www.sqlite.org>
   [testify]: <https://github.com/stretchr/testify>
   
