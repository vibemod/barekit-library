# Library Template Specification

This repository serves as a **template/stub for AI-based library generation** in the Contributte ecosystem. AI agents should use this as a reference when generating new PHP libraries.

## Purpose

This template provides:
- Standardized file structure for Contributte libraries
- Placeholder variables (`{{VAR}}`) for customization
- Example code patterns (DI extension, service, tests)
- Pre-configured CI/CD workflows
- Quality assurance tooling setup

---

## Template Variables

All placeholders use the `{{VARIABLE}}` format (double curly braces).

| Variable | Description | Example Values | Used In |
|----------|-------------|----------------|---------|
| `{{ORGANIZATION}}` | Vendor/organization name (lowercase) | `nettrine`, `contributte`, `apitte` | composer.json, README.md, ruleset.xml, src/*.php |
| `{{PROJECT}}` | Project name (lowercase) | `orm`, `console`, `middlewares` | composer.json, README.md, ruleset.xml, src/*.php |
| `{{DESCRIPTION}}` | Package description | `Doctrine ORM integration for Nette` | composer.json |
| `{{KEYWORDS}}` | Composer keywords (repeat for multiple) | `nette`, `doctrine`, `orm` | composer.json |
| `{{PHP_MIN_VERSION}}` | Minimum PHP version | `8.2`, `8.3` | composer.json, phpstan.neon, tests.yml |
| `{{PHP_VERSION}}` | Default PHP version for CI | `8.3` | phpstan.yml, codesniffer.yml, tests.yml |
| `{{PHP_MAX_VERSION}}` | Maximum PHP version to test | `8.4` | tests.yml |
| `{{PHPSTAN_LEVEL}}` | PHPStan strictness level (0-9) | `9` | phpstan.neon |
| `{{YEAR}}` | Copyright year | `2025` | LICENSE |

---

## File Structure

```
barekit-library/
├── .docs/
│   └── README.md              # Detailed documentation
├── .github/
│   └── workflows/
│       ├── codesniffer.yml    # Code style CI
│       ├── coverage.yml       # Coverage reporting
│       ├── phpstan.yml        # Static analysis CI
│       └── tests.yml          # Test runner CI
├── src/
│   ├── DI/
│   │   └── ExampleExtension.php   # Example compiler extension
│   └── ExampleService.php         # Example service class
├── tests/
│   ├── Cases/
│   │   └── ExampleTest.phpt       # Example test
│   └── bootstrap.php              # Test bootstrap
├── .editorconfig              # Editor configuration
├── .gitattributes             # Git export rules
├── .gitignore                 # Git ignore rules
├── composer.json              # Composer configuration
├── LICENSE                    # MIT license
├── Makefile                   # Build commands
├── phpstan.neon               # PHPStan configuration
├── README.md                  # Main readme
├── ruleset.xml                # CodeSniffer rules
└── SPECS.md                   # This file (AI hints)
```

---

## File References

Quick links to all template files:

### Configuration Files
- [composer.json](composer.json) - Package definition with placeholders
- [phpstan.neon](phpstan.neon) - Static analysis config
- [ruleset.xml](ruleset.xml) - Code style rules
- [Makefile](Makefile) - Build commands
- [.editorconfig](.editorconfig) - Editor settings
- [.gitignore](.gitignore) - Ignored files
- [.gitattributes](.gitattributes) - Export rules

### Documentation
- [README.md](README.md) - Main project readme
- [.docs/README.md](.docs/README.md) - Detailed documentation

### Source Code Examples
- [src/DI/ExampleExtension.php](src/DI/ExampleExtension.php) - DI extension pattern
- [src/ExampleService.php](src/ExampleService.php) - Service class pattern

### Test Examples
- [tests/bootstrap.php](tests/bootstrap.php) - Test environment setup
- [tests/Cases/ExampleTest.phpt](tests/Cases/ExampleTest.phpt) - Test case pattern

### CI/CD Workflows
- [.github/workflows/tests.yml](.github/workflows/tests.yml) - Test runner
- [.github/workflows/phpstan.yml](.github/workflows/phpstan.yml) - Static analysis
- [.github/workflows/codesniffer.yml](.github/workflows/codesniffer.yml) - Code style
- [.github/workflows/coverage.yml](.github/workflows/coverage.yml) - Coverage

### Legal
- [LICENSE](LICENSE) - MIT license template

---

## Generation Checklist

When generating a new library from this template, follow this checklist:

### 1. Replace All Placeholders
- [ ] `{{ORGANIZATION}}` - Set vendor name
- [ ] `{{PROJECT}}` - Set project name
- [ ] `{{DESCRIPTION}}` - Write package description
- [ ] `{{KEYWORDS}}` - Add relevant keywords
- [ ] `{{PHP_MIN_VERSION}}` - Set minimum PHP (usually `8.2`)
- [ ] `{{PHP_VERSION}}` - Set CI PHP version (usually `8.3`)
- [ ] `{{PHP_MAX_VERSION}}` - Set max test PHP (usually `8.4`)
- [ ] `{{PHPSTAN_LEVEL}}` - Set analysis level (usually `9`)
- [ ] `{{YEAR}}` - Set current year

### 2. Update Source Files
- [ ] Rename `ExampleExtension.php` to `{{PROJECT}}Extension.php`
- [ ] Update class name inside the extension file
- [ ] Rename/replace `ExampleService.php` with actual services
- [ ] Add real implementation code
- [ ] Create proper directory structure (DI/, Exception/, etc.)

### 3. Update Tests
- [ ] Rename/replace `ExampleTest.phpt` with actual tests
- [ ] Add test mocks in `tests/Mocks/` if needed
- [ ] Ensure tests cover main functionality

### 4. Update Documentation
- [ ] Rewrite `.docs/README.md` with actual usage docs
- [ ] Add configuration examples
- [ ] Add code examples
- [ ] Update version table in `README.md`

### 5. Finalize
- [ ] Remove `SPECS.md` (it's for template use only)
- [ ] Run `make install` to install dependencies
- [ ] Run `make qa` to verify code quality
- [ ] Run `make tests` to verify tests pass

---

## Quality Checklist

Before committing, ensure:

### Code Standards
- [ ] `make cs` passes (CodeSniffer)
- [ ] `make phpstan` passes (static analysis)
- [ ] `make tests` passes (all tests green)

### File Hygiene
- [ ] No hardcoded project-specific values remain
- [ ] All placeholders properly replaced
- [ ] No example/stub code in production files
- [ ] Proper PSR-4 autoloading configured

### Documentation
- [ ] README.md has correct badges
- [ ] Installation instructions are accurate
- [ ] Usage examples are working
- [ ] Version table is up to date

---

## Standards Reference

This template follows the Contributte Library Development Specification:

**Source:** https://raw.githubusercontent.com/contributte/.github/refs/heads/master/specs/LIBRARY.md

### Key Standards
- **PHP Version:** 8.2+ minimum
- **Nette Framework:** 3.2+
- **PHPStan Level:** 9 (strictest)
- **Test Framework:** Nette Tester
- **Code Style:** Contributte QA ruleset

### Git Conventions
- Use rebase-based workflow (no merge commits)
- Atomic commits in imperative mood ("Add feature", not "Added feature")
- AI contributions use `ai@f3l1x.io` email

### Required Make Targets
```bash
make install   # Install dependencies
make qa        # Run all quality checks
make cs        # Run CodeSniffer
make csf       # Fix code style automatically
make phpstan   # Run static analysis
make tests     # Run tests
make coverage  # Generate coverage report
```

### Required Dependencies

All Contributte libraries MUST use these dev dependencies:

| Package | Purpose | Required |
|---------|---------|----------|
| `contributte/tester` | Test utilities wrapper | **Yes** |
| `contributte/qa` | Code style ruleset | **Yes** |
| `contributte/phpstan` | PHPStan configuration | **Yes** |

**Important:** Do NOT replace `contributte/tester` with raw `nette/tester`. The wrapper provides:
- `Contributte\Tester\Environment` for test setup
- `Contributte\Tester\Toolkit` for test organization
- Consistent patterns across all Contributte libraries

---

## Example Usage

### For AI Agents

When asked to create a new library (e.g., "Create a library for Redis caching"):

1. **Clone this template structure**
2. **Replace placeholders:**
   ```
   {{ORGANIZATION}} → contributte
   {{PROJECT}} → redis
   {{DESCRIPTION}} → Redis caching integration for Nette
   {{KEYWORDS}} → nette, redis, cache
   {{PHP_MIN_VERSION}} → 8.2
   {{PHP_VERSION}} → 8.3
   {{PHP_MAX_VERSION}} → 8.4
   {{PHPSTAN_LEVEL}} → 9
   {{YEAR}} → 2025
   ```
3. **Create actual implementation:**
   - `src/DI/RedisExtension.php`
   - `src/RedisClient.php`
   - `src/Cache/RedisCache.php`
   - etc.
4. **Write tests:**
   - `tests/Cases/DI/RedisExtensionTest.phpt`
   - `tests/Cases/RedisCacheTest.phpt`
5. **Update documentation**
6. **Run quality checks**

---

## Notes for AI Agents

1. **Always check existing patterns** - Look at the example files for coding style
2. **Use proper namespacing** - Follow PSR-4 with `{{ORGANIZATION}}\{{PROJECT}}\` prefix
3. **Prefer tabs for indentation** - As defined in `.editorconfig`
4. **Use strict types** - All PHP files must have `declare(strict_types=1);`
5. **Follow Nette conventions** - DI extensions, services, etc.
6. **Write comprehensive tests** - Use Nette Tester with `.phpt` files
7. **Keep dependencies minimal** - Only add what's truly needed
8. **Document thoroughly** - Both inline and in `.docs/README.md`

---

## Removing Template Artifacts

When the library is ready for production, remove:
- [ ] `SPECS.md` (this file)
- [ ] Example files if not replaced:
  - `src/DI/ExampleExtension.php`
  - `src/ExampleService.php`
  - `tests/Cases/ExampleTest.phpt`