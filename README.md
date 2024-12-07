# Chiphpotle Symfony Bundle

This package integrates the [Chiphpotle Rest](https://github.com/alsbury/chiphpotle-rest) SpiceDB client
into Symfony, and makes it available as a service. This is a bare-bones integration that only provides the raw client.

Install using:

```shell
composer require thewunder/chiphpotle-bundle
```

Configure your rest connection in config/packages/chiphpotle.yaml

```yaml
chiphpotle:
    base_url: http
    secret: SuperSecrit
```

And then it will be available for auto-wiring in your classes, assuming you have symfony flex enabled.

```php
use Chiphpotle\Rest\Client;
use Chiphpotle\Rest\Model\CheckPermissionRequest;
use Chiphpotle\Rest\Model\ObjectReference;
use Chiphpotle\Rest\Model\SubjectReference;
use Chiphpotle\Rest\Enum\Permissionship;

class MyPermissionService
{
    public function __construct(private readonly Client $spiceDB)
    {
    }
    
    public function check(ObjectReference $object, string $permission, SubjectReference $subject): bool
    {
        $response = $this->spiceDB->checkPermission(new CheckPermissionRequest($object, $permission, $subject));
        return $response->getPermissionship() == Permissionship::HAS_PERMISSION;
    }
    
    //...
```
