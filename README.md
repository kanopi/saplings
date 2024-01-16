# Saplings - Drupal Build Starter Recipe

This recipe is designed to help start a build project.

Rather than one large Recipe that tries to do everything, we've broken it up
into multiple sub-recipes.  This recipe installs them all, but you can also
install the sub-recipes on their own.

* [kanopi/gin-admin-experience](https://github.com/kanopi/gin-admin-experience)
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

**Note** 
Redis will need to be setup through multiple steps and PRs. You must:
1. Enable module and pantheon, leave redis config commented out, push to a PR, and merge
2. Create a new branch/PR, uncomment redis config and push

## Roadmap

### Phase 1
  * [kanopi/saplings-content-types](https://github.com/kanopi/saplings-content-types) - Currently a Post and Page content type and dependencies
    * [kanopi/saplings-content-base](https://github.com/kanopi/saplings-content-base) - Dependencies and field storage for content recipes.
  * [kanopi/saplings-theme](https://github.com/kanopi/saplings-theme) - Recipe that configures https://www.drupal.org/project/ui_suite_bootstrap and dependencies.
  * [kanopi/saplings-components](https://github.com/kanopi/saplings-components) - Paragraphs
    * [kanopi/saplings-components-base](https://github.com/kanopi/saplings-components-base) - based dependencies for Paragraphs
* [kanopi/solr-search-pantheon-recipe](https://github.com/kanopi/solr-search-pantheon-recipe) - Recipe that installs essential modules for Pantheon SOLR search.

### Phase 2

* Break Content type and Component types into their own recipes. Once this [Drupal issue](https://www.drupal.org/project/distributions_recipes/issues/3390916) is resolved.
* Event/Calendar

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

To reset after you have done some testing:

* Run `fin init`
* The build will fail with the following message as we haven't installed Drupal yet. `Error: Class "Drupal\user\Entity\User" not found`
* Run `fin drush si minimal -y && fin drush uli` to install Drupal and log in.

---

### Requiring recipes
Use composer the require the recipes needed.  We currently host on our packagist.

#### Saplings suite
* [kanopi/saplings](https://packagist.org/packages/kanopi/saplings)
  * [kanopi/gin-admin-experience](https://packagist.org/packages/kanopi/gin-admin-experience) - Installs and configures the Gin admin theme and supporting base modules.
  * [kanopi/saplings-base](https://packagist.org/packages/kanopi/saplings-base) - Simple base configuration for modern Drupal.
  * [kanopi/saplings-editorial](https://packagist.org/packages/kanopi/saplings-editorial) - Configures a rich editing experience for modern Drupal.
  * [kanopi/saplings-launch](https://packagist.org/packages/kanopi/saplings-launch) - Configures best practices for launching modern Drupal.
  * [kanopi/saplings-media](https://packagist.org/packages/kanopi/saplings-media) - Configures best practices for media.
    * [kanopi/imagemagick-configuration](https://packagist.org/packages/kanopi/imagemagick-configuration) - Configures default Drupal image toolkit.
   
#### Other Recipes:
* [kanopi/password-policy-90-days](https://packagist.org/packages/kanopi/password-policy-90-days) - Installs and configures Password Policy and sets a 90 day expiration default.

---

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
2. Apply each of the sub-saplings recipes by themselves and in different combinations.

Follow the instructions above to get a local environment spun up.
Then run the following commands to require and apply the recipe.
`fin composer require kanopi/saplings-content-types` (for example)
`fin recipe-apply saplings-content-types`


  * Do they function properly?
  * In each, what Drupal configuration are missing? Things you need to click together to launch your site.
  * In each, what Drupal modules are missing?
  * In each, what do they have that you think should be removed?
  * In each, do you see opportunity to subdivide even more by functionality to make these even more choose-your-own-adventure for developers?
3. General input and feedback welcome!
4. What are your ideas for additional recipes?

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
