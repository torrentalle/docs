---
title: Contributing To Orchestra Platform

---

1. [Introduction](#introduction)
2. [Security Vulnerabilities](#security-vulnerabilities)
3. [Pull Requests](#pull-requests)
4. [Feature Requests](#feature-requests)
5. [Template for Pull Request, Proposal, Request or Bugfixes](#templates)
6. [Coding Guidelines](#coding-guidelines)

<a name="introduction"></a>
## Introduction

Orchestra Platform is free, open-source software, meaning anyone can contribute to its development and progress. Orchestra Platform source code is currently hosted on [Github](https://github.com), which provides an easy method for forking the project and merging your contributions.

<a name="security-vulnerabilities"></a>
## Security Vulnerabilities

If you discover a security vulnerability within Orchestra Platform, please send an e-mail to security@orchestraplatform.com. All security vulnerabilities will be promptly addressed.

<a name="pull-requests"></a>
## Pull Requests

The pull request process differs for new features and bugs. Before sending a pull request for a new feature, you should first create an issue with `[Proposal]` in the title. The proposal should describe the new feature, as well as implementation ideas. The proposal will then be reviewed and either approved or denied. Once a proposal is approved, a pull request may be created implementing the new feature. Pull requests which do not follow this guideline will be closed immediately.

### Pull Request for Bugfixes

Pull requests for bugs may be sent without creating any proposal issue. If you believe that you know of a solution for a bug that has been filed on Github, please leave a comment detailing your proposed fix.

### Unit Testing

A pull request or bugfixes **should** include relevant test cases to ensure that Orchestra Platform work as expected and avoid regression bug is produced in the future.

<a name="feature-requests"></a>
## Feature Requests

If you have an idea for a new feature you would like to see added to Orchestra Platform, you may create an issue on Github with `[Request]` in the title. The feature request will then be reviewed by a core contributor.

<a name="templates"></a>
## Template for Pull Request, Proposal, Request or Bugfixes

Please include the following template when opening an issue on Github:

```markdown
| Q             | A
| ------------- | ---
| Bug fix?      | [yes|no]
| New feature?  | [yes|no]
| BC breaks?    | [yes|no]
| Deprecations? | [yes|no]
| Tests pass?   | [yes|no]
| Fixed tickets | [comma separated list of tickets fixed by the PR]
| License       | MIT
| Doc PR        | [The reference to the documentation PR if any]
```

<a name="coding-guidelines"></a>
## Coding Guidelines

Orchestra Platform follows the [PSR-0](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md), [PSR-1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md) and [PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md) coding standards. In addition to these standards, below is a list of other coding standards that should be followed:

* Namespace declarations should be on the same line as `<?php`.
* Preferable to use `&&` and `||` instead of `and` or `or`.
* Trait names are suffixed with `Trait (FooTrait)`.

We also include `.php_cs` file on each repository which would allow you to run `php-cs-fixer fix` if you have [PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer) install locally.
