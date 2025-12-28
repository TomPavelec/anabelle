![](https://heatbadger.now.sh/github/readme/contributte/anabelle/?deprecated=1)

<p align=center>
    <a href="https://bit.ly/ctteg"><img src="https://badgen.net/badge/support/gitter/cyan"></a>
    <a href="https://bit.ly/cttfo"><img src="https://badgen.net/badge/support/forum/yellow"></a>
    <a href="https://contributte.org/partners.html"><img src="https://badgen.net/badge/sponsor/donations/F96854"></a>
</p>

<p align=center>
    Website 🚀 <a href="https://contributte.org">contributte.org</a> | Contact 👨🏻‍💻 <a href="https://f3l1x.io">f3l1x.io</a> | Twitter 🐦 <a href="https://twitter.com/contributte">@contributte</a>
</p>

## Disclaimer

| :warning: | This project is no longer being maintained. |
|---|---|

| Composer | [`contributte/anabelle`](https://packagist.org/packages/contributte/anabelle) |
|---|---|
| Version | ![](https://badgen.net/packagist/v/contributte/anabelle) |
| PHP | ![](https://badgen.net/packagist/php/contributte/anabelle) |
| License | ![](https://badgen.net/github/license/contributte/anabelle) |

<p align=center>
	<img src="https://github.com/contributte/anabelle/blob/master/assets/anabelle.png">
</p>

## About

Anabelle is a JSON-RPC API documentation generator. It supports both JSON-RPC and REST architectures and provides an extended Markdown syntax for creating rich, interactive API documentation.

## Usage

To install the latest version of `contributte/anabelle` use [Composer](https://getcomposer.org).

```bash
composer require contributte/anabelle
```

## How to use anabelle

```bash
cd myApi
composer require contributte/anabelle
vendor/bin/anabelle docs-src docs
```

### CLI options

#### Automatically overwrite output directory

```bash
vendor/bin/anabelle docs-src docs -o
// Or
vendor/bin/anabelle docs-src docs --overwriteOutputDir
```

#### Add http auth to generated files

**Beware! Anabelle generates by default .html files. If you are using http auth, it generates .php files due to the need of validating http auth headers.**

```bash
vendor/bin/anabelle docs-src docs -u user -p pass
// Or
vendor/bin/anabelle docs-src docs --httpAuthUser user -httpAuthPass pass
```

## Extended Markdown syntax

### `#include <file.md>`

```md
#include variables.md
```

### `$variable = <value>`

```md
$uuid = 123e4567-e89b-12d3-a456-426655440000
```

Inline variable usage

```md
User uuid is {$uuid}
```

### `$$blockVariable ... $$`

```md
$$successEmptyResponse
{
	"jsonrpc": "2.0",
	"result": {},
	"id": null
}
$$
```

Block variable usage

```md
Server returns response:

{$$successEmptyResponse}
```

### `@ <sectionName>:<sectionFile.md>`

High-level section definition. This macro available only in `index.md` file.

```md
@ Home:home.md
@ About project:about.md
```

### `@@ <sectionName>:<sectionFile.md>`

Method section definition. This macro available only in `index.md` file.

```md
@@ user.login:methods/user.login.md
@@ user.logout:methods/user.logout.md
@@ user.register:methods/user.register.md
@@ user.confirm-registration:methods/user.confirm-registration.md
```

### `[File link](foo/bar/data.json)`

[File link](foo/bar/data.json) will create a link to file (`foo/bar/data.json`). The file will be copied to documentation output directory for safety reasons.

```md
[File link](foo/bar/data.json)
[Project root directory file link](../app/schema/user.json)
```

## Generator workflow

1. Most important (and only required) file is `index.md`. In this file, you can use only (different Markdown markup is ignored in `index.md`):
	- `# <h1>`
	- `## <h2>`
	- `#include <file.md>`
	- `$variable = <value>`
	- `$$blockVariable ... $$`
	- `@ <sectionName>:<sectionFile.md>`
	- `@@ <sectionName>:<sectionFile.md>`)
1. `#include` macros are replaced
1. `<h1>` is used as documentation page title (only the first found one is used)
1. `<h2>` can be used wherever you want in the sidebar
1. `@` and `@@` sections are rendered in the sidebar nav
1. Content of `@` and `@@` sections is rendered into separate files and loaded into the main section detail after clicking particular section link in the nav

## Examples

- http://github.com/contributte/playground/tree/master/contributte-anabelle (example project)
- https://examples.contributte.org/packages/anabelle/ (generated documentation)
- https://github.com/contributte/playground (playground)
- https://contributte.org/examples.html (more examples)

## Versions

| State  | Version  | Branch   | Nette  | PHP     |
|--------|----------|----------|--------|---------|
| dev    | `^6.0.0` | `master` | `3.0+` | `>=8.1` |
| stable | `^5.0.0` | `master` | `3.0+` | `>=8.1` |

## Development

This package was maintained by these authors.

<a href="https://github.com/paveljanda">
	<img width="80" height="80" src="https://avatars2.githubusercontent.com/u/1488874?v=3&s=80">
</a>

-----

Consider to [support](https://contributte.org/partners.html) **contributte** development team.
Also thank you for using this package.
