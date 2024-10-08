# ENG version

# TaigaAPI Python Client

TaigaAPI is a Python client for interacting with the Taiga REST API. This library provides a simple interface for managing projects, issues, epics, user stories, and attachments within the Taiga project management platform.

## Installation

To install TaigaAPI, clone the repository and install the dependencies:

```bash
git clone https://github.com/alextanker/taiga-client.git
cd taiga-client
pip install -r requirements.txt
```
or
```bash
pip install taiga-client
```

# Usage

## Initialization

To start using TaigaAPI, create an instance of the TaigaAPI class by providing the server IP, username, and password.

```python
from taiga_client import TaigaAPI

taiga = TaigaAPI(serverIp="your-server-ip", username="your-username", password="your-password")
```

## Methods

getProjectBySlug(slug: str) -> SimpleNamespace
Fetches a project by its slug.

```python
project = taiga.getProjectBySlug("project-slug")
print(project.id, project.name)
```

createIssue(projectID: int, subject: str, description: str, type: int, priority: int, status: int, tags: List[str] = []) -> SimpleNamespace
Creates an issue in a specific project.

```python
project = taiga.getProjectBySlug("project-slug")

issue = taiga.createIssue(projectID=project.id, subject="Bug", description="A critical bug", type=1, priority=2, status=1)
print(issue.id, issue.subject)
```

createEpic(projectID: int, subject: str, description: str, status: int, tags: List[str] = []) -> SimpleNamespace
Creates an epic in a specific project.

```python
project = taiga.getProjectBySlug("project-slug")

epic = taiga.createEpic(projectID=project.id, subject="New Feature", description="A new feature description", status=1)
print(epic.id, epic.subject)
```

createUserstory(projectID: int, subject: str, description: str, status: int, swimlane: int = -1, tags: List[str] = []) -> SimpleNamespace
Creates a user story in a specific project.

```python
project = taiga.getProjectBySlug("project-slug")

userstory = taiga.createUserstory(projectID=project.id, subject="User Story", description="User story description", status=1)
print(userstory.id, userstory.subject)
```

createAttachmentForIssue(projectID: int, issueID: int, attachmentPath: str, fromComment=False) -> SimpleNamespace
Creates an attachment for a specific issue.

```python
project = taiga.getProjectBySlug("project-slug")

attachment = taiga.createAttachmentForIssue(projectID=project.id, issueID=42, attachmentPath="path/to/file.png")
print(attachment.id)
```

getPriorityList(projectID: int) -> SimpleNamespace
Returns a list of priority objects for issues in a project.

```python
project = taiga.getProjectBySlug("project-slug")

priorities = taiga.getPriorityList(projectID=project.id)
for priority in priorities:
    print(priority.name)
```

getStatusIssueList(projectID: int) -> SimpleNamespace
Returns a list of possible statuses for issues in a project.

```python
statuses = taiga.getStatusIssueList(projectID=1)
for status in statuses:
    print(status.name)
```

createIssueComment(issueID: int, text: str) -> requests.Response
Creates a comment for a specific issue.

```python
response = taiga.createIssueComment(issueID=42, text="This is a comment.")
print(response.status_code)
```

## More Methods

The library includes more methods for managing epics, user stories, attachments, and more. Please refer to the source code for the full list of available methods.

# RU версия

# TaigaAPI Python Client

TaigaAPI — это Python клиент для взаимодействия с Taiga REST API. Эта библиотека предоставляет простой интерфейс для управления проектами, задачами, эпиками, пользовательскими историями и вложениями в платформе управления проектами Taiga.

## Установка

Для установки TaigaAPI клонируйте репозиторий и установите зависимости:

```bash
git clone https://github.com/alextanker/taiga-client.git
cd taiga-client
pip install -r requirements.txt
```
или
```bash
pip install taiga-client
```
# Использование

## Инициализация

Чтобы начать использовать TaigaAPI, создайте экземпляр класса TaigaAPI, указав IP сервера, имя пользователя и пароль.

```python
from taiga_client import TaigaAPI

taiga = TaigaAPI(serverIp="your-server-ip", username="your-username", password="your-password")
```

## Методы

getProjectBySlug(slug: str) -> SimpleNamespace
Получает проект по его слагу.

```python
project = taiga.getProjectBySlug("project-slug")
print(project.id, project.name)
```

createIssue(projectID: int, subject: str, description: str, type: int, priority: int, status: int, tags: List[str] = []) -> SimpleNamespace
Создает задачу в определенном проекте.

```python
project = taiga.getProjectBySlug("project-slug")

issue = taiga.createIssue(projectID=project.id, subject="Bug", description="A critical bug", type=1, priority=2, status=1)
print(issue.id, issue.subject)
```

createEpic(projectID: int, subject: str, description: str, status: int, tags: List[str] = []) -> SimpleNamespace
Создает эпик в определенном проекте.

```python
project = taiga.getProjectBySlug("project-slug")

epic = taiga.createEpic(projectID=project.id, subject="New Feature", description="A new feature description", status=1)
print(epic.id, epic.subject)
```

createUserstory(projectID: int, subject: str, description: str, status: int, swimlane: int = -1, tags: List[str] = []) -> SimpleNamespace
Создает пользовательскую историю в определенном проекте.

```python
project = taiga.getProjectBySlug("project-slug")

userstory = taiga.createUserstory(projectID=project.id, subject="User Story", description="User story description", status=1)
print(userstory.id, userstory.subject)
```

createAttachmentForIssue(projectID: int, issueID: int, attachmentPath: str, fromComment=False) -> SimpleNamespace
Создает вложение для определенной задачи.

```python
project = taiga.getProjectBySlug("project-slug")

attachment = taiga.createAttachmentForIssue(projectID=project.id, issueID=42, attachmentPath="path/to/file.png")
print(attachment.id)
```

getPriorityList(projectID: int) -> SimpleNamespace
Возвращает список приоритетов для задач в проекте.

```python
project = taiga.getProjectBySlug("project-slug")

priorities = taiga.getPriorityList(projectID=project.id)
for priority in priorities:
    print(priority.name)
```

getStatusIssueList(projectID: int) -> SimpleNamespace
Возвращает список возможных статусов для задач в проекте.

```python
statuses = taiga.getStatusIssueList(projectID=1)
for status in statuses:
    print(status.name)
```

createIssueComment(issueID: int, text: str) -> requests.Response
Создает комментарий для определенной задачи.

```python
response = taiga.createIssueComment(issueID=42, text="This is a comment.")
print(response.status_code)
```

## Дополнительные Методы

Библиотека включает больше методов для управления эпиками, пользовательскими историями, вложениями и многим другим. Ознакомьтесь с исходным кодом для полного списка доступных методов.

# License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.