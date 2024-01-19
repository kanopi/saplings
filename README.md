# Saplings - Drupal Build Starter Recipe

This recipe is designed to help start a build project.

Rather than one large Recipe that tries to do everything, we've broken it up
into multiple sub-recipes.  This recipe installs them all, but you can also
install the sub-recipes on their own.

* [kanopi/gin-admin-experience](https://github.com/kanopi/gin-admin-experience)
* [kanopi/saplings-base](https://github.com/kanopi/saplings-base)
* [kanopi/saplings-editorial](https://github.com/kanopi/saplings-editorial)
* [kanopi/saplings-launch](https://github.com/kanopi/saplings-launch)
* [kanopi/saplings-content-types](https://github.com/kanopi/saplings-content-types)
  * [kanopi/saplings-media](https://github.com/kanopi/saplings-media)
  * [kanopi/saplings-content-base](https://github.com/kanopi/saplings-content-base) - Dependencies and field storage for content recipes.
  * [kanopi/saplings-component-types](https://github.com/kanopi/saplings-component-types) - Paragraphs
    * [kanopi/saplings-component-base](https://github.com/kanopi/saplings-component-base) - Dependencies for Paragraphs

## Installation

Apply a recipe to Drupal installed with a minimal profile.

- Clone the [kanopi/drupal-starter](https://github.com/kanopi/drupal-starter) repository and give the project folder a unique name to avoid collision with the base drupal-starter repository.
- Edit the `docksal.env` and change the line `hostingsite="pantheon_project_machine_name"` to the name of your project folder.
- Example: `hostingsite="sapling-test-project"`.
- Initialize the site using `fin init`.
- The project will fail at the `fin drush uli` step as there is no Drupal install yet.
- After the `fin drush uli` failure, install Drupal with the Minimal profile using the `fin drush si minimal` command.
- Run `fin composer require kanopi/saplings` to require this repository.
- Note: If you run into an error about dropzone.js then use the following command instead `fin composer require kanopi/saplings:^0.1.31`.
- Run `fin recipe-apply saplings` to apply this recipe.
- If you are using this on a project, run `fin recipe-unpack kanopi/saplings` to unpack the dependencies from this
recipe to the site project's composer.json file.  This is not required for testing.

## Roadmap

### Phase 1
* [kanopi/saplings-theme](https://github.com/kanopi/saplings-theme) - Recipe that configures https://www.drupal.org/project/ui_suite_bootstrap and dependencies.
* [kanopi/solr-search-pantheon-recipe](https://github.com/kanopi/solr-search-pantheon-recipe) - Recipe that installs essential modules for Pantheon SOLR search.
* Profile Content Type

### Phase 2

* Break Content type and Component types into their own recipes. Once this [Drupal issue](https://www.drupal.org/project/distributions_recipes/issues/3390916) is resolved.
* Event/Calendar

### Other Recipes:
* [kanopi/password-policy-90-days](https://packagist.org/packages/kanopi/password-policy-90-days) - Installs and configures Password Policy and sets a 90 day expiration default.

## Contributing/Testing
We'd love your help with testing, ideation, and development.

### Setting up a quick testing environment
Decide on a name for your testing environment.  In this example, I will use `kanland`.

* Checkout kanopi/drupal-starter into it's own repo.
* `git clone git@github.com:kanopi/drupal-starter.git kanland && cd kanland`
* Open /.docksal/docksal.env in your editor.
* Update row 28 `hostingsite="kanland"` and save.
* Run `fin init`
* The build will fail with the following message as we haven't installed Drupal yet. `Error: Class "Drupal\user\Entity\User" not found`
* Run `fin drush si minimal -y && fin drush uli` to install Drupal and log in.
* Click on the one-time-login to verify the minimal install happened.
* Require this repository: `fin composer require kanopi/saplings:^0.1.31`
* Apply the recipe: `fin recipe-apply saplings`

To reset after you have done some testing:

* Run `fin init`
* The build will fail with the following message as we haven't installed Drupal yet. `Error: Class "Drupal\user\Entity\User" not found`
* Run `fin drush si minimal -y && fin drush uli` to install Drupal and log in.

---

### Requiring recipes
Use composer the require the recipes needed.  We currently host on our packagist.

### Applying and Unpacking recipes in Drupal
To apply contrib/composer installed recipes, run the following commands:

`fin recipe-apply recipe-name`

Each recipe can have composer dependencies. "Unpacking" takes these dependencies from the recipe and applies them to the project's composer.json file.

To unpack contrib/composer installed recipes, run the following commands:

`fin recipe-unpack recipe-name`

---

### Testing scenarios

1. kanopi/saplings

Follow the instructions above to get a local environment spun up.
Then run the following commands to require and apply the recipe.
`fin composer require kanopi/saplings`
`fin recipe-apply saplings`

  * Does it function properly?
  * What Drupal configuration are missing? Things you need to click together to launch your site.
  * What Drupal modules are missing?
  * What does it have that you think should be removed?

~~2. Apply each of the sub-saplings recipes by themselves and in different combinations.~~

Once this [Drupal issue](https://www.drupal.org/project/distributions_recipes/issues/3390916) is resolved, we can do this.

~~Follow the instructions above to get a local environment spun up.~~
~~Then run the following commands to require and apply the recipe.~~
~~`fin composer require kanopi/saplings-content-types` (for example)~~
~~`fin recipe-apply saplings-content-types`~~


~~* Do they function properly?~~
~~* In each, what Drupal configuration are missing? Things you need to click together to launch your site.~~
~~* In each, what Drupal modules are missing?~~
~~* In each, what do they have that you think should be removed?~~
~~* In each, do you see opportunity to subdivide even more by functionality to make these even more choose-your-own-adventure for developers?~~
~~3. General input and feedback welcome!~~
~~4. What are your ideas for additional recipes?~~

---

### Add Recipe functionality to your project
If you like what you see here, you can add recipe support to your project today!

* Copy `recipe-apply`, `recipe-configure`, and `recipe-unpack` from /.docksal/commands/ to your project.
* If you don't have any patches:
  * Run `fin recipe-config` in the CLI of your project to configure composer and patch Drupal core.
* If you do have patches:
  * Comment out rows 30 and 31 of /.docksal/commands/recipe-config
  * Save and run the command
  * Apply the Drupal recipes patch manually.
  * `fin composer update drupal/core-*`
* Follow the suggestions at the end of the command.
* You're ready to start applying recipes.

Note: The Drupal core patch is experimental, but it is mainly additions.  If you don't want to have that on your production site, the good news is that you don't have to have patch after you've applied and unpacked your recipes.  You can simply remove the patch and update core as the recipes are now yours.
