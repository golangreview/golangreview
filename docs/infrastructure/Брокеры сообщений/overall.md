---
title: Общие вопросы
sidebar_position: 1
---

## Exactly Once
Exactly Once означает, что каждое сообщение будет обработано ровно один раз. Это достигается путем гарантии, что каждое сообщение будет доставлено и обработано ровно один раз, без дубликатов и без пропусков. Для достижения этой гарантии необходимо использовать транзакции и идемпотентные операции. В контексте Kafka, это может быть достигнуто с помощью Kafka Streams или Kafka Connect, которые поддерживают транзакции и идемпотентные операции.

## At Least Once
At Least Once означает, что каждое сообщение будет обработано по крайней мере один раз. Это гарантирует, что каждое сообщение будет обработано, но может быть обработано более одного раза в случае сбоев или повторных доставок. Это обычно достигается путем повторной доставки сообщений в случае сбоев. В Kafka, это может быть достигнуто с помощью настройки enable.idempotence для производителей и processing.guarantee для Kafka Streams.

## At Most Once
At Most Once означает, что каждое сообщение будет обработано не более одного раза. Это гарантирует, что каждое сообщение будет обработано не более одного раза, но может быть пропущено в случае сбоев. Это обычно достигается путем отключения повторной доставки сообщений и использования неидемпотентных операций. В Kafka, это может быть достигнуто с помощью настройки enable.idempotence для производителей и processing.guarantee для Kafka Streams, но с осторожностью, так как это может привести к потере сообщений.

## Что такое Push и Pull модель поведения брокеров сообщений?

Push и Pull модели поведения брокеров сообщений определяют способ доставки сообщений от брокера к клиенту.

- **Push модель**: В Push модели брокер активно отправляет сообщения клиенту, когда они становятся доступными. Клиент не запрашивает сообщения у брокера, а брокер отправляет их клиенту по мере появления. Push модель обеспечивает низкую задержку и высокую производительность, так как сообщения доставляются немедленно.

- **Pull модель**: В Pull модели клиент запрашивает сообщения у брокера, когда он готов их обработать. Клиент опрашивает брокера и получает сообщения, которые были отправлены в момент запроса. Pull модель обеспечивает гибкость и контроль над процессом получения сообщений, так как клиент сам решает, когда и какие сообщения получать.

Push и Pull модели могут использоваться в различных системах обмена сообщениями в зависимости от требований к производительности и надежности.

## Что такое Pub/Sub модель обмена сообщениями?

Pub/Sub (Publish/Subscribe) модель обмена сообщениями - это архитектурный шаблон, который позволяет отправителям (публикаторам) и получателям (подписчикам) обмениваться сообщениями через посредника (брокера).

- **Публикаторы (Publishers)**: Публикаторы отправляют сообщения в темы (топики) брокера. Темы - это категории сообщений, которые группируются по схожим характеристикам или темам. Публикаторы не знают, кто будет получать сообщения, они просто отправляют их в темы.

- **Подписчики (Subscribers)**: Подписчики получают сообщения из тем брокера, на которые они подписаны. Подписчики могут подписываться на несколько тем и получать сообщения, которые соответствуют их интересам. Подписчики не знают, откуда именно приходят сообщения, они просто получают их из тем.

- **Брокер (Broker)**: Брокер - это посредник между публикаторами и подписчиками. Брокер принимает сообщения от публикаторов и отправляет их подписчикам в соответствии с их подписками. Брокер обеспечивает масштабируемость, надежность и гарантии доставки сообщений между публикаторами и подписчиками.

Pub/Sub модель обмена сообщениями широко используется в распределенных системах для обмена сообщениями между компонентами и обеспечения асинхронной связи.
