---
title: Микросервисы
sidebar_position: 1
---

## Что такое микросервисы?

Микросервисная архитектура – это подход к разработке ПО, где приложение разбивается на множество независимых, слабосвязанных микросервисов. Каждый сервис выполняет определенную функцию и автономно работает в своем процессе.

```mermaid 
graph LR
    A(Клиент/Пользователь) --> B(API-шлюз)
    B(API-шлюз) --> C(Сервис 1)
    C(Сервис 1) --> D(База данных)
    B(API-шлюз) --> E(Сервис 2)
    E(Сервис 2) --> F(База данных)
```

### Преимущества
- Масштабируемость: Легко добавлять, удалять или масштабировать отдельные сервисы.
- Независимость: Разработка и развертывание каждого сервиса происходят независимо.
- Надежность: Отказ одного сервиса не влияет на работу других.
- Простота обслуживания: Легче найти и исправить ошибки в небольших сервисах.

### Недостатки
- Сложность разработки: Требует более сложного проектирования и управления.
- Сложность тестирования: Нужно тестировать не только каждый сервис, но и их взаимодействие.
- Увеличение накладных расходов: Больше сервисов – больше сетевых запросов, больше инфраструктуры.

----- 

## Какие паттерны проектирования используются в микросервисной архитектуре?

- API Gateway: Этот паттерн используется для маршрутизации запросов к соответствующим микросервисам. API Gateway действует как единая точка входа в систему, обеспечивая аутентификацию, авторизацию, логирование, мониторинг и обработку ошибок.
- Service Discovery: Сервисы в микросервисной архитектуре могут динамически добавляться или удаляться. Service Discovery позволяет сервисам находить друг друга без необходимости вручную настраивать сетевые адреса.
- Circuit Breaker: Этот паттерн предотвращает запросы к сервису, который уже не отвечает, предотвращая таким образом каскадные сбои в системе.
- CQRS (Command Query Responsibility Segregation): Разделение операций чтения и записи данных на разные модели позволяет оптимизировать производительность и масштабируемость системы.
- Event Sourcing: Вместо хранения текущего состояния системы, сохраняется последовательность событий, которые приводят к этому состоянию. Это позволяет легко - восстанавливать состояние системы и анализировать историю изменений.
- Saga Pattern: Используется для управления распределенными транзакциями, позволяя выполнять последовательности локальных транзакций, каждая из которых может быть отменена, если что-то пойдет не так.

## Чем микросервисы отличаются от монолитной архитектуры?

1. Структура приложения
    - Монолитная архитектура: Приложение разрабатывается как единое целое, где все компоненты тесно связаны и работают вместе в рамках одного процесса. Это может быть как одно приложение, так и несколько взаимосвязанных приложений, работающих в рамках одного проекта.
    - Микросервисная архитектура: Приложение разбивается на множество независимых сервисов, каждый из которых выполняет свою функцию и может быть разработан, развернут и масштабирован независимо от остальных.
2. Масштабирование
    - Монолитная архитектура: Масштабирование обычно происходит путем добавления больше ресурсов (например, CPU, память) к одному экземпляру приложения. Это может быть неэффективно, если только одна часть приложения требует больше ресурсов.
    - Микросервисная архитектура: Масштабирование происходит на уровне отдельных сервисов, что позволяет оптимизировать использование ресурсов и улучшить производительность.
3. Разработка и развертывание
    - Монолитная архитектура: Изменения в любой части приложения требуют пересборки и перезапуска всего приложения, что может быть затратно по времени и ресурсам.
    - Микросервисная архитектура: Изменения в одном сервисе не влияют на другие, что позволяет быстро и независимо разрабатывать, тестировать и развертывать отдельные сервисы.
4. Технологический стек
    - Монолитная архитектура: Обычно использует один технологический стек для всего приложения, что может ограничивать выбор технологий.
    - Микросервисная архитектура: Позволяет использовать разные технологии для разных сервисов, что может улучшить производительность и гибкость системы.
5. Управление данными
    - Монолитная архитектура: Данные обычно хранятся в одной базе данных, что может привести к проблемам с производительностью и масштабируемостью.
    - Микросервисная архитектура: Каждый сервис может иметь свою собственную базу данных, что позволяет оптимизировать структуру данных под конкретные потребности каждого сервиса.
6. Отказоустойчивость
    - Монолитная архитектура: Сбой в одной части приложения может привести к сбою всего приложения.
    - Микросервисная архитектура: Отдельные сервисы могут быть изолированы друг от друга, что позволяет системе продолжать работать даже при сбоях в некоторых сервисах.
7. Сложность
    - Монолитная архитектура: Обычно проще в разработке, тестировании и развертывании из-за единой кодовой базы и технологического стека.
    - Микросервисная архитектура: Вводит дополнительную сложность из-за необходимости управления множеством сервисов, обеспечения их взаимодействия и координации.