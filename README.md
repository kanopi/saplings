# Saplings - Drupal Build Starter Recipe

This recipe is designed to help start a highly configured Drupal project.

Rather than one large Recipe that tries to do everything, we've broken it up
into multiple sub-recipes.  This recipe installs them all, but you can also
install the sub-recipes on their own (Once this [Drupal issue](https://www.drupal.org/project/distributions_recipes/issues/3390916)
 is resolved.).

* [kanopi/gin-admin-experience](https://github.com/kanopi/gin-admin-experience)
* [kanopi/saplings-base](https://github.com/kanopi/saplings-base)
* [kanopi/saplings-editorial](https://github.com/kanopi/saplings-editorial)
* [kanopi/saplings-launch](https://github.com/kanopi/saplings-launch)
* [kanopi/saplings-content-types](https://github.com/kanopi/saplings-content-types)
  * [kanopi/saplings-media](https://github.com/kanopi/saplings-media)
    * [kanopi/saplings-images](https://github.com/kanopi/saplings-images)
    * [kanopi/imagemagick-configuration](https://github.com/kanopi/imagemagick-configuration)
  * [kanopi/saplings-content-base](https://github.com/kanopi/saplings-content-base)
  * [kanopi/saplings-component-types](https://github.com/kanopi/saplings-component-types)
    * [kanopi/saplings-component-base](https://github.com/kanopi/saplings-component-base)
* [kanopi/saplings-theme](https://github.com/kanopi/saplings-theme)

## Requiring and Applying this recipe

Apply a recipe to Drupal installed with a minimal profile.  See [below](#setting-up-a-quick-testing-environment)
 is you want to set up a quick testing environment.

- Follow the instructions in [kanopi/drupal-starter](https://github.com/kanopi/drupal-starter)
 to start a new project as it is configured for recipes and tooling needed.
- Run `fin composer require kanopi/saplings:^0.1.38` to require this repository.
- Run `fin recipe-apply saplings` to apply this recipe.
- Run `fin recipe-unpack kanopi/saplings` to unpack the dependencies from this
recipe to the site project's composer.json file.
- Export configuration.

You can then remove the recipe once it has been applied and unpacked as the
configuration is now in your Drupal, and the dependencies are in your composer.

- `fin composer remove kanopi/saplings`
- Export configuration.

## Roadmap

### Phase 1
* [kanopi/solr-search-pantheon-recipe](https://github.com/kanopi/solr-search-pantheon-recipe)
 - Recipe that installs essential modules for Pantheon SOLR search.


### Phase 2

* Profile Content type
* Event Content type/Supporting Views


### Development notes:
* Break Content type and Component types into their own recipes. Once this [Drupal issue](https://www.drupal.org/project/distributions_recipes/issues/3390916) is resolved.


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

### Add Recipe functionality to an existing project
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
