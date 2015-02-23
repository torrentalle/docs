---
title: Authorization Component

---

Authorization Component gives you the ability to create custom ACL metrics which is unique to each of your extension/application. The component works best with [Auth Component]({doc-url}/components/auth) but you could as well implements `Orchestra\Contracts\Auth\Guard`.

In most other solutions, you are either restrict to file based configuration for ACL or only allow to define a single metric for your entire application. This simplicity would later become an issue depends on how many extensions do you have within your application.

* [Version Compatibility](#compatibility)
* [Installation](#installation)
* [Configuration](#configuration)
* [Usage](#usage)
  - [Concept of RBAC](#concept-of-rbac)
  - [Creating a New ACL Instance](#creating-a-new-acl-instance)
  - [Verifying the ACL](#verifying-the-acl)

## Version Compatibility {#compatibility}

Laravel    | Authorization
:----------|:----------
 5.0.x     | 3.0.x

 ## Installation

 To install through composer, simply put the following in your `composer.json` file:

 ```json
 {
    "require": {
        "orchestra/authorization": "3.0.*"
    },
    "repositories": [
        {
            "type": "vcs",
            "url": "https://github.com/orchestral/authorization.git"
        }
    ]
}
```

And then run `composer install` from the terminal.

## Configuration {#configuration}

Next add the service provider in `config/app.php`.

```php
'providers' => [

    // ...
    'Orchestra\Authorization\AuthorizationServiceProvider',
    'Orchestra\Memory\MemoryServiceProvider',

    'Orchestra\Memory\CommandServiceProvider',
],
```

### Aliases

To make development easier, you could add `Orchestra\Support\Facades\ACL` alias for easier reference:

```php
'aliases' => [

    'ACL' => 'Orchestra\Support\Facades\ACL',

],
```

## Usage {#usage}

* [Concept of RBAC](#concept-of-rbac)
* [Creating a New ACL Instance](#creating-a-new-acl-instance)
* [Verifying the ACL](#verifying-the-acl)

### Concept of RBAC {#concept-of-rbac}

Name     | Description
:--------|:-----------------------
actions  | Actions is either route or activity that we as a user can do (or not do).
roles    | Roles are user group that a user can belong to.
acl      | Is a boolean mapping between actions and roles, which determine whether a role is allow to do an action.

### Creating a New ACL Instance {#creating-a-new-acl-instance}

```php
<?php

ACL::make('acme');
```

Imagine we have a **acme** extension, above configuration is all you need in your extension/application service provider.

### Verifying the ACL {#verifying-the-acl}

To verify the created ACL, you can use the following code.

```php
$acl = ACL::make('acme');

if (! $acl->can('manage acme')) {
    return redirect()->to(handles('orchestra::login'));
}
```

Or you can create a route filter.

```php
Route::filter('foo.manage', function () {
    if (! ACL::make('acme')->can('manage acme')) {
        return redirect()->to(handles('orchestra::login'));
    }
});
```