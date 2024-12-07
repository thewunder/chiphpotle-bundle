# Chiphpotle Symfony Bundle

This package integrates the [Chiphpotle Rest](https://github.com/alsbury/chiphpotle-rest) SpiceDB client
into Symfony, and makes it available as a service.

Install using:

```shell
composer require thewunder/chiphpotle-bundle
```

Configure your rest connection in config/packages/chiphpotle.yaml

```yaml
chiphpotle:
    base_url: http
    secret: secretFrom starting
```

And then it will be available for auto-wiring in your classes, assuming you have symfony flex enabled.
