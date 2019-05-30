Eclectic
=====

A theme for high performance customizable hugo websites.

![Eclectic Theme](theme.jpg?raw=true "Eclectic Theme")

    NOTE: REQUIRES ATTRIBUTION IN FOOTER TO STAY INTACT FOR USAGE.

See [atishay.me](https://github.com/atishay/atishay.github.io) for sample website.

## Layout Types

* `default` No neeed to enter the type parameter. Default is a blog post.
* `simple` Used for pages where the content does not have a sidebar, just header, rendered markdown and footer. Supported front matter additions
  * `subtitle` For subtitle.
* `contact` Used for Contact Us pages.
* `meta` Special page type for having sections and nested content. Used to create the home page. See metapages below for usage.

## Images
* `assets/image/favicon.svg` - Favicon SVG Version
* `assets/image/favicon.png` - Favicon PNG Version
* `assets/image/logo.svg` or `assets/image/logo.*` - Logo

## Menus

* `top` - Top menu shown in the header. Supports one nested level of submenus. Uses the Section name to find the appropriate top level item to highlight.

## Template blocks

* `favicon` - Present in the `<head>` tag. Defaults to basic favicon and basic apple touch icon support.
* `social` - All the data for open graph, twitter cards and JSON-LD. Contains sub-blocks
    * `opengraph` - For Open Graph tags
    * `meta` - General meta tags like description and canonical url.
    * `jsonld` - JSON-LD for Google.

## Footer

* The footer contains up to sections that can be specified in the front matter. The template has special column arrangement for the sectioning as defined below.
* There can be modified in the settings as an array in `Site.Params.Footer` with the following options

    * `title` - Title of the section.
    * `content` - In Markdown
    * `image` - Show an image in the section (by default pulled to the left with 50% width).
    * `recent` - Name of the section to show recents from.
    * `recentCount` - Count for the recent range.
    * `contact` - Optimized version of the contact us snippets. The order and contents are not customizable as you can still use markdown to make a custom version.

## Column arrangements

CSS Grids are used for column arrangements in the most logical manner.

* 1 - Single Item
* 2 - Two items till `md`
* 3 - Three items till `lg`
* 4 - 4 items till `xl`, 2 2 till `md`
* 5 - 2 3 till `lg`, 2 2 1 till `md`
* 6 - 3 3 till `lg`, 2 2 2 till `md`
* 7 - 3 4 till `xl`, 3 3 1 till `lg`, 2 2 2 1 till `md`
* 8 - 4 4 till `xl`, 2 2 2 2 till `md`
* 9 - 3 3 3 till `lg`
* 12 - 4 4 4 till `xl`, 3 3 3 3 till `lg`, 2 2 2 2 2 2 till `md`

8 and 9 can be further improved if needed.

## Settings

* `Site.Params.CSP` Set true to enable CSP. *Please test with production environment flag with this*. In production prevents live reload.
* `Site.Params.colorPickerEnabled` Enable color picker to help the user switch color themes as well as dark mode.
* `Site.Params.checksDarkMode` - Should enable automatic switching to dark mode based on media query.
* `Site.Params.custom_css` - Custom CSS File for overrides.
* `Site.Params.github` - Github link for the octocat on top right.
* `Site.Params.custom_css` - Custom CSS Overrides file.
* `Site.Author` - Contains `facebook`, `twitter`, `github`, `email`,  `linkedin` and `name` fields.
* `Site.Params.color` - Default theme color.
* `Site.Params.description` - Default Description.
* `Site.Params.sidebar` - Shared sidebar for all posts. Will be available under the post specific sidebar.
* `Site.Params.sharedHeader` - List of sections where the header has no changes (like blogs unless we have a submenu). This cached headers to improve performance.
* `Site.Params.Tex` - tex2svg hosted location.
* `Site.Params.Guitar` - guitar2svg hosted location.

## Browsers

* This theme uses all modern CSS like CSS Variables, CSS Grid and flexbox. Do not expect this to support older browsers.

## Posts

* Use Hugo Page Bundles for posts. The theme expects each page to have a beautiful image.

## Top Matter

* `sidebar` - You can add stuff to the page sidebar by using a the front matter and passing a list to `sidebar` with `title` and `content` properties. `content` can be markdown.
* `coverAnchor` - Add anchoring position for the cover image.

## Shortcodes

* `fig` Same as `figure`, but added support for responsive resizing of images.
* `tex` Renders Latex as SVG. Optional parameter `inline` for inline latex. Needs `Site.Params.Tex` for the `tex2svg` hosting.
* `guitar` Renders guitar tabs and chords using jtab. Needs `Site.Params.Guitar` for the `guitar2svg` hosting.

## Metapages
Metapages are pages built using structured data and provide advanced styling and grouping into columns, support for carousels, lists etc. In the front matter for a meta page, you can supply the following information to render structured data:
* `title` The title of the section
* `subtitle` Section's subtitle
* `image` Top level image for the section:
  * `href` relative location fo the image inside assets folder.
  * `alt` Alt text to the image
  * `width` Desired width
  * `height` Desired height
* `content` Markdown content
* `icon` Section icon (Can be a file relative to assets or a fontawesome name eg link for `fa-link`)
* `items` List of items to display in the section. Each item contains the following:
  * `title` Item's title
  * `content` Markdown content of the item
  * `image` Image for the item. Contains the following:
    * `href` relative location
    * `width` desired width
    * `height` desired height
    * `alt` Alt text to the image
    * `anchor` Anchor location for resizing the image
  * `attribution` Markdown content for image attribution.
  * `icon` Contains the item's icon. Consists of:
    * `href` relative location
    * `alt` Alt text
    * `width` Element width
    * `height` Element height
* `type` Section type. Can be one fo the following:
  * Unspecified content grouped into columns as described in column arrangement.
  * `left-image` Full sized image floated to the left.
  * `item-icon-left` Icon is shown to the left of the item in the grid
  * `full-width` Each item takes full width instead of being placed in the grid.
  * `max-2` Alternate grid with maximum items specified each row to be 2.
  * `filter` Provides a filter list. The top level has additional parameter called `filter` for the default filter. Each item has a a space separated list of filters in a field called `filter` applicable to the item.
  * `blog` to show recent blog entries. Has additional parameters `count` which is the number of blog items and `section` which is the name of the section to get recent posts from.
  * `carousel` Provides support for running a carousel of content.
  * `centered` Provides content centered on the page behind the background image supplied as `background`
