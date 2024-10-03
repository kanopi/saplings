![saplings](https://github.com/kanopi/saplings/assets/5177009/a6377e32-deb2-49d8-873a-f3dd5a36fa7c)

# Components

## Component Style Options Overview

![alt_text](assets/images/components-style-options.png "Style options")

Each paragraph comes with a set of styles that can be updated for the display of that section. The styles are nested in a dropdown section below each of the paragraph edit forms. Included styles are listed below.

- **Margin**

  Options:
    * Top and Bottom Small
    * Top and Bottom Medium
    * Top and Bottom Large
    * Top Small
    * Top Medium
    * Top Large
    * Bottom Small
    * Bottom Medium
    * Bottom Large
- **Padding**

  Options:
    * Top and Bottom Small
    * Top and Bottom Medium
    * Top and Bottom Large
    * Top Small
    * Top Medium
    * Top Large
    * Bottom Small
    * Bottom Medium
    * Bottom Large
- **Container**

  Options:
    * Standard (this is the standard container width)
    * Container Fluid (this will cause the container to be full width
- **Width**

  Options:
    * 75%
    * 50%
    * 33%
    * 25%
- **Background**

  Options:
    * Primary
    * Secondary
    * Dark
    * Light

The default options can be altered after installation. Currently the only options that have default settings are:
- Padding: Top and Bottom Medium
- Container: Standard


## Accordion/Accordion Item

![alt_text](assets/images/component-accordion.png "Accordion")

The accordion component allows you to place text in expandable sections that are collapsed by default.

1. To add an accordion paragraph type, create a new Page content.
2. From the Components dropdown, choose an accordion.
3. Add a Header and a description if you would like.
4. Add individual Accordion Items.
5. Styles that are set on the Accordion will affect the entire accordion section.


## Block

![alt_text](assets/images/component-block.png "Block")

The Block component allows you to place a Drupal block inline with other content.

1. To add a Block paragraph type, create a new Page content.
2. From the Components dropdown, choose a Block.
3. Add a Header and a description if you would like.
4. Choose the block that you would like to display.
5. Styles that are set on the Block will affect the entire Block section.


## Card

![alt_text](assets/images/component-card.png "Card")

Use the card component to create flexible and extensible content containers that can link to local or external pages.

1. To add a Card paragraph type, when editing Page content, from the Components dropdown, choose a Card.
2. Add a Header for the Card Title and a description for the card body
3. Add media for the card image
4. Add a link to display a link in the card footer.

### For Developers:

To alter the display of your card to Horizontal, go to the Manage Display Tab, Click on Pattern Settings, and for the Variant dropdown, choose Horizontal.

![alt_text](assets/images/component-card-horizontal-variant.png "Card Horizontal Variant")

To alter the display of the link for your card, in the Manage display tab, Edit the pattern variant for the link. The Variant determines which bootstrap button style variable will be printed.

![alt_text](assets/images/component-card-link-variant.png "Card Link Variant")

In addition, there is a setting that allows you to link the entire card, or to turn that off.

![alt_text](assets/images/component-card-link-card.png "Card Link Entire Card")


## Carousel/Carousel Item

![alt_text](assets/images/component-carousel.png "Carousel Component")

A Carousel component allows for multiple media items to be displayed in a carousel

The carousel settings are defined by the Carousel Pattern being used on the Manage Display page of the paragraph. /admin/structure/paragraphs_type/sa_carousel/display

The Carousel Item field is using the pattern of Carousel.

Available options are:
* With Controls
* With Indicators
* With touch Swiping
* Token for Interval
* ID

![alt_text](assets/images/component-carousel-settings.png "Carousel Settings")

The referenced Carousel Item Paragraph type is using the pattern of Carousel Item which has the following slots:

* Image
* Caption

To manage the display, visit this URL `admin/structure/paragraphs_type/sa_carousel_item/display`

On the display page you can also alter the image style that is loaded.

![alt_text](assets/images/component-carousel-image-style.png "Carousel Component Image Size")


## Columns

![alt_text](assets/images/component-columns.png "Columns COmponent")

A columns component allows for a text, card, block, media, carousel and block component to be added as columns..


## Filtered List

A filtered list component allows you to display preselected Drupal views.


## Hero

The hero components allows for either a background video or image and a text overlay.


## Media

![alt_text](assets/images/component-columns.png "Media Component")

A media component allows for either an image or video media entity to be added.


## Tabs

![alt_text](assets/images/component-tabs.png "Tabs Component")

A tabs component allows for multiple tabs to be added to display content in a tabbed display that will show and hide tabbed content on click.


## Text

![alt_text](assets/images/component-text.png "Text Component")

A text component allows for text to be added to a page with a wysiwyg editor.


## Side By Side

![alt_text](assets/images/component-side-by-side.png "Side by Side Component")

The side by side component offers a header, text field and a media field for displaying the content. The default display of content is the Media on the left and the Header and Description on the right. The columns will display as equal columns. If the Boolean for Reverse Order is turned on, The Media will display on the right side instead.

