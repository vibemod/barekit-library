p# {{ORGANIZATION}}/{{PROJECT}}

{{DESCRIPTION}}

## Content

- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Examples](#examples)

## Installation

Install package using composer.

```bash
composer require {{ORGANIZATION}}/{{PROJECT}}
```

Register the extension in your `config.neon` file.

```neon
extensions:
  {{PROJECT}}: {{ORGANIZATION}}\{{PROJECT}}\DI\{{PROJECT}}Extension
```

## Configuration

### Minimal configuration

```neon
{{PROJECT}}:
  # Add minimal configuration here
```

### Advanced configuration

Here is the list of all available options with their types.

```neon
{{PROJECT}}:
  # option1: <type>
  # option2: <type>
```

## Usage

### Basic usage

```php
<?php declare(strict_types=1);

use {{ORGANIZATION}}\{{PROJECT}}\ExampleService;

$service = $container->getByType(ExampleService::class);
$service->doSomething();
```

### Advanced usage

```php
// Add advanced usage examples here
```

## Examples

> [!TIP]
> Take a look at more examples in [contributte/playground](https://github.com/contributte/playground).