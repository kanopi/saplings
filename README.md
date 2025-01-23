![saplings](https://github.com/kanopi/saplings/assets/5177009/a6377e32-deb2-49d8-873a-f3dd5a36fa7c)

# Saplings - Drupal Build Starter Recipe

This recipe is designed to help start a highly configured Drupal project.

Rather than one large Recipe that tries to do everything, we've broken it up
into multiple sub-recipes.  This recipe installs them all, but you can also
install the sub-recipes on their own.

* [kanopi/gin-admin-experience](https://github.com/kanopi/gin-admin-experience)
* [kanopi/saplings-base](https://github.com/kanopi/saplings-base)
* [kanopi/saplings-editorial](https://github.com/kanopi/saplings-editorial)
* [kanopi/saplings-launch](https://github.com/kanopi/saplings-launch)
* [kanopi/saplings-tests](https://github.com/kanopi/saplings-tests) [Cypress]
* [kanopi/saplings-content-types](https://github.com/kanopi/saplings-content-types)
  * [kanopi/saplings-content-base](https://github.com/kanopi/saplings-content-base)
  * [kanopi/saplings-component-types](https://github.com/kanopi/saplings-component-types)
    * [kanopi/saplings-component-base](https://github.com/kanopi/saplings-component-base)
      * [kanopi/saplings_paragraphs](https://github.com/kanopi/saplings_paragraphs) [Module]
  * [kanopi/saplings-media](https://github.com/kanopi/saplings-media)
    * [kanopi/imagemagick-configuration](https://github.com/kanopi/imagemagick-configuration)
  * [kanopi/saplings-theme](https://github.com/kanopi/saplings-theme)
    * [kanopi/saplings_child](https://github.com/kanopi/saplings_child) [Theme]
  * [kanopi/saplings_custom](https://github.com/kanopi/saplings_custom) [Module]


---

<!-- Created in Lucid at https://lucid.app/lucidchart/6711555d-82fc-4ea0-8cd2-9f1c65ecb4b0/edit -->
![Saplings ERD](https://github.com/kanopi/saplings/assets/5177009/3b348086-bfcd-427e-adf5-c6bcd1fc2cc7)



---

## Requiring and Applying this recipe

Apply a recipe to Drupal installed with a minimal profile.  See [below](#setting-up-a-quick-testing-environment)
 is you want to set up a quick testing environment.

- Follow the instructions in [kanopi/drupal-starter](https://github.com/kanopi/drupal-starter)
 to start a new project as it is configured for recipes and tooling needed.
- Run `fin composer require kanopi/saplings:^1` to require this repository.
- Run `fin recipe-apply ../recipes/saplings` to apply this recipe.
- Run the following command to unpack the dependencies from all kanopi/saplings recipes to the site project's composer.json file.
```
fin recipe-unpack kanopi/saplings && fin recipe-unpack kanopi/gin-admin-experience && fin recipe-unpack kanopi/saplings-base && fin recipe-unpack kanopi/saplings-editorial && fin recipe-unpack kanopi/saplings-launch && fin recipe-unpack kanopi/saplings-content-types && fin recipe-unpack kanopi/saplings-component-types && fin recipe-unpack kanopi/saplings-component-base && fin recipe-unpack kanopi/saplings-content-base && fin recipe-unpack kanopi/saplings-media && fin recipe-unpack kanopi/imagemagick-configuration && fin recipe-unpack kanopi/saplings-theme && fin recipe-unpack kanopi/saplings-editorial
```
- Export configuration.

You can then remove the recipe once it has been applied and unpacked as the
configuration is now in your Drupal, and the dependencies are in your composer.

- `fin composer remove kanopi/saplings`
- Export configuration.


---

## Roadmap

### Phase 1
Feature complete.

### Phase 2
* Break Page and Post Content types into their own recipes.
* Additional components as needed.
* [kanopi/saplings-ai](https://github.com/kanopi/saplings-ai) - [WIP] Helpful AI functionality for content creators.
* [kanopi/saplings-person](https://github.com/kanopi/saplings-person) - [WIP] Creates a Person content type and related configuration.
* [kanopi/saplings-events](https://github.com/kanopi/saplings-events) -  [WIP] Configuration for Saplings Events 
* [kanopi/saplings-demo-events](https://github.com/kanopi/saplings-demo-events) - [WIP] Demo content for Saplings Events
* [kanopi/solr-search-pantheon-recipe](https://github.com/kanopi/solr-search-pantheon-recipe) - The goal is to configure Solr for Pantheon on a site that isn't going to use saplings.

### Phase 3
Investigate extending Drupal CMS' recipes.

### Other Kanopi Recipes:
* [kanopi/saplings-domain](https://github.com/kanopi/saplings-domain) -  Installs and configures Domain modules.
* [kanopi/saplings-demo-content](https://github.com/kanopi/saplings-demo-content) - Demo content for Saplings.
* [kanopi/saplings-solr](https://github.com/kanopi/saplings-solr) - Configures a back-end and front-end Solr search customized for Saplings on Pantheon.
* [kanopi/password-policy-90-days](https://packagist.org/packages/kanopi/password-policy-90-days) - Installs and configures Password Policy and sets a 90 day expiration default.
* [kanopi/remote-video-youtube-lite](https://packagist.org/packages/kanopi/remote-video-youtube-lite) - Configures Remote Video Media entity to use Lite YouTube Embed.

### Other Saplings related modules
* [kanopi/saplings_navbar](https://github.com/kanopi/saplings_navbar) - Creates a navbar pattern for Saplings that allows the parent to be a link and then have a dropdown indicator to access child menu items.

---

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
* Require this repository: `fin composer require kanopi/saplings:^1`
* Apply the recipe: `fin recipe-apply saplings`

To reset after you have done some testing:

* Run `fin init`
* The build will fail with the following message as we haven't installed Drupal yet. `Error: Class "Drupal\user\Entity\User" not found`
* Run `fin drush si minimal -y && fin drush uli` to install Drupal and log in.

### Requiring recipes
Use composer the require the recipes needed.  We currently host on our packagist.

### Applying and Unpacking recipes in Drupal
To apply contrib/composer installed recipes, run the following commands:

`fin recipe-apply recipe-name`

Each recipe can have composer dependencies. "Unpacking" takes these dependencies from the recipe and applies them to the project's composer.json file.

To unpack contrib/composer installed recipes, run the following commands:

`fin recipe-unpack recipe-name`


---

Note: The Drupal core patch is experimental, but it is mainly additions.  If you don't want to have that on your production site, the good news is that you don't have to have patch after you've applied and unpacked your recipes.  You can simply remove the patch and update core as the recipes are now yours.


## Dependency Graph

<img width="1775" alt="saplings-graph" src="https://github.com/kanopi/saplings/assets/5177009/1f1c9c31-0a20-4e7f-8c76-aa0c108f6d59">

Created using [JBZoo/Composer-Graph](https://github.com/JBZoo/Composer-Graph)
