# Drupal Build Starter Recipe

This recipe is designed to help start a build project.

## Installation

- Follow the instructions in the drupal-starter repository.
- Install Drupal with the Minimal profile.
- Require this repository using composer.
- Run `fin recipe-apply drupal-build-starter` to apply this recipe.
- Run `fin recipe-unpack kanopi/drupal-build-starter` to unpack the dependencies
 from this recipe to the site project's composer.json file.

**Note** 
Redis will need to be setup through multiple steps and PRs. You must:
1. Enable module and pantheon, leave redis config commented out, push to a PR, and merge
2. Create a new branch/PR, uncomment redis config and push

## Contributing

### Adding a module

1. Add the module and any version requirements in the `require` section of composer.json.
2. Enable the module in the `install` section of the recipe.yml.
3. If your module has configuration you want to import, do so in the `config > import` section of the recipe.yml.
