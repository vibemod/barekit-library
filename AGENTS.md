# Guidelines

This is a Contributte library for Nette Framework. It provides reusable components that integrate with Nette's dependency injection container.

## Development Commands

### Setup

```bash
make install        # Install composer dependencies
```

### Quality Assurance

```bash
make qa             # Run all checks (cs + phpstan)
make cs             # Check code style with PHP CodeSniffer
make csf            # Fix code style automatically
make phpstan        # Run static analysis
```

### Testing

```bash
make tests          # Run all tests with Nette Tester
make coverage       # Generate code coverage report
```

Tests use Nette Tester framework with `.phpt` files in `tests/Cases/`. Each test file must end with `(new TestClass())->run();` to execute.

## Dev Dependencies

- **contributte/qa** - Code style ruleset for PHP CodeSniffer
- **contributte/tester** - Wrapper above nette/tester with utilities
- **contributte/phpstan** - Preconfigured PHPStan with strict rules

## Architecture

### Nette DI Integration

Libraries integrate with Nette via **compiler extensions**. Extensions live in `src/DI/` and extend `Nette\DI\CompilerExtension`. They register services during container compilation.

Key methods:
- `loadConfiguration()` - Register services and process config
- `beforeCompile()` - Modify services before container freezes

### Service Layer

Business logic lives in service classes under `src/`. Services are registered via the DI extension and can be autowired into presenters, commands, or other services.

### Exception Handling

Custom exceptions extend base PHP exceptions and live in `src/Exception/`. Use `LogicException` for programming errors, `RuntimeException` for runtime failures.

## Coding Style

### PHP Standards

- Strict types required: `<?php declare(strict_types=1);`
- Tabs for indentation (not spaces)
- PSR-4 autoloading
- Final classes preferred for leaf classes

### Nette Conventions

- DI extensions named `{Project}Extension`
- Service definitions use `$this->prefix('name')` for unique naming
- Configuration accessed via `$this->getConfig()`

### Test Style

Tests use `Toolkit::test()` with static functions:
```php
Toolkit::test(static function (): void {
	Assert::true($value);
	Assert::same($expected, $actual);
});
```

Use `TestCase` class only in special cases when instructed by user (e.g., tests requiring setUp/tearDown or shared state).

## External References

- Nette DI: https://doc.nette.org/en/dependency-injection
- Nette Tester: https://tester.nette.org/
- Contributte: https://contributte.org/
