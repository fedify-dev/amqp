<!-- deno-fmt-ignore-file -->

@fedify/amqp: AMQP/RabbitMQ driver for Fedify
=============================================

> [!IMPORTANT]
> This repository is obsolete and has been archived in favor of the monorepo
> [fedify-dev/fedify].

[![JSR][JSR badge]][JSR]
[![npm][npm badge]][npm]
[![GitHub Actions][GitHub Actions badge]][GitHub Actions]

> [!NOTE]
>
> Although it's theoretically possible to be used with any AMQP 0-9-1 broker,
> this package is primarily designed for and tested with [RabbitMQ].

This package provides [Fedify]'s [`MessageQueue`] implementation for AMQP, which
is supported by RabbitMQ:

 -  [`AmqpMessageQueue`]

Here is an example of how to use it:

~~~~ typescript
import { createFederation } from "@fedify/fedify";
import { AmqpMessageQueue } from "@fedify/amqp";
import { connect } from "amqplib";

const federation = createFederation({
  queue: new AmqpMessageQueue(await connect("amqp://localhost")),
  // ... other configurations
});
~~~~

The `AmqpMessageQueue` constructor accepts options as the second
parameter, which can be used to configure the message queue:

~~~~ typescript
new AmqpMessageQueue(await connect("amqp://localhost"), {
  queue: "my_queue",
})
~~~~

For more details, please refer to the docs of [`AmqpMessageQueueOptions`].

[fedify-dev/fedify]: https://github.com/fedify-dev/fedify
[JSR]: https://jsr.io/@fedify/amqp
[JSR badge]: https://jsr.io/badges/@fedify/amqp
[npm]: https://www.npmjs.com/package/@fedify/amqp
[npm badge]: https://img.shields.io/npm/v/@fedify/amqp?logo=npm
[GitHub Actions]: https://github.com/fedify-dev/amqp/actions/workflows/main.yaml
[GitHub Actions badge]: https://github.com/fedify-dev/amqp/actions/workflows/main.yaml/badge.svg
[RabbitMQ]: https://www.rabbitmq.com/
[Fedify]: https://fedify.dev/
[`KvStore`]: https://jsr.io/@fedify/fedify/doc/federation/~/KvStore
[`MessageQueue`]: https://jsr.io/@fedify/fedify/doc/federation/~/MessageQueue
[`AmqpMessageQueue`]: https://jsr.io/@fedify/amqp/doc/mq/~/AmqpMessageQueue
[`AmqpMessageQueueOptions`]: https://jsr.io/@fedify/amqp/doc/mq/~/AmqpMessageQueueOptions


Installation
------------

### Deno

~~~~ sh
deno add @fedify/amqp
~~~~

### Node.js

~~~~ sh
npm install @fedify/amqp
~~~~

### Bun

~~~~ sh
bun add @fedify/amqp
~~~~


Changelog
---------

### Version 0.4.0

To be released.

### Version 0.3.0

Released on June 25, 2025.

 -  Added `nativeRetrial` option to `AmqpMessageQueueOptions` to enable
    native retrial of messages.

 -  The type of the `AmqpMessageQueue()` constructor's first parameter has been
    changed from `Connection` to `ChannelModel`.

### Version 0.2.0

Released on March 28, 2025.

 -  Added `AmqpMessageQueue.enqueueMany()` method for efficiently enqueuing
    multiple messages at once.

 -  Updated *@js-temporal/polyfill* to 0.5.0 for Node.js and Bun. On Deno,
    there is no change because the polyfill is not used.

### Version 0.1.0

Initial release.  Released on October 14, 2024.
