# Saplings - Drupal Build Starter Recipe

This recipe is designed to help start a build project.

Rather than one large Recipe that tries to do everything, we've broken it up
into multiple sub-recipes.  This recipe installs them all, but you can also
install the sub-recipes on their own.

* [kanopi/saplings-base](https://github.com/kanopi/saplings-base)
* [kanopi/saplings-media](https://github.com/kanopi/saplings-media)
* [kanopi/saplings-editorial](https://github.com/kanopi/saplings-editorial)
* [kanopi/saplings-launch](https://github.com/kanopi/saplings-launch)

## Installation

- Follow the instructions in the
[kanopi/drupal-starter](https://github.com/kanopi/drupal-starter) repository.
- Install Drupal with the Minimal profile.
- Run `fin composer require kanopi/saplings` to require this repository.
- Run `fin recipe-apply saplings` to apply this recipe.
- Run `fin recipe-unpack kanopi/saplings` to unpack the dependencies from this
recipe to the site project's composer.json file.

## Contributing

### Adding a module

1. Add the module and any version requirements in the `require` section of
composer.json.
2. Enable the module in the `install` section of the recipe.yml.
3. If your module has configuration you want to import, do so in the
`config > import` section of the recipe.yml.
