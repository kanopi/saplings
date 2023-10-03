# Drupal Build Starter Recipe

This recipe is designed to help start a build project.  In is configured to do
the following:

- Install the best parts of the Standard Drupal install profile.
- Disable core modules.
- Install and configure commonly used contrib modules.

## Installation

- Follow the instructions in the drupal-starter repository.
- Install Drupal with the Minimal profile.
- Require this repository using composer.
- Run `fin recipe-apply drupal-build-starter` to apply this recipe.
- Run `fin recipe-unpack kanopi/drupal-build-starter` to unpack the dependencies
 from this recipe to the site project's composer.json file.
