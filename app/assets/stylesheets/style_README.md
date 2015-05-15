stylesheets_README.md

We will be using towards a OOCSS, SMACSS, BEM model.





/*------------------------------------*
    #GUIDES AND READING
 *------------------------------------*/

General Style Guide
http://cssguidelin.es/

Using OOCSS, SMACSS, and BEM
https://mattstauffer.co/blog/organizing-css-oocss-smacss-and-bem

OOCSS
http://thesassway.com/intermediate/using-object-oriented-css-with-sass

SMACSS
https://smacss.com/book/

BEM
http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/





/*------------------------------------*
    #STRUCTURE
 *------------------------------------*/

# style.scss
Core file: imports the others.

# _base.scss
Includes normalize.css, and also sets styles on base elements: html, body, a, ul, li, etc.

# _layout.scss
Depending on the complexity of the site, we will likely have a file dedicated to layout. Grids, responsive frameworks, wrappers, etc. all live here.

# _modules.scss
Includes definitions for our modules, or objects. The goal is for as much code to exist in here as possible, making it flexible and reusable. This file will just be a list of modules defined (and documented) one after another.

#_other.scss
The name for this partial varies, but essentially this is all the code that doesn't fit in _base, _layout, or _modules. Code we just couldn't make modular; glue between modules; top level layouts; etc.

#_shame.scss
Also from CSS Wizardry (see CSS Wizardry's post on shame.css), a _shame file is something we've been trying out only recently. This file is a place where you put all the code you're not proud of, with the intention of A) isolating it and B) fixing it later. The goal is for this file to be empty, but some times you just have to throw that hack in there to get it working.

We may also add a _javascript.scss if we're not using Gulp or Grunt to concatenate the styles for our Javascript plugins.

Structure should look like this:

stylesheets/
|
|-- base/                 # Base elements
|   |-- _base.scss        # Include to get all modules
|   |                       imports for all mixins + global project variables
|   |-- _typography.scss  # typography
|   |-- _reset.scss       # reset
|   ...
|
|-- layout/               # The layout of the sections
|   |-- _layout.scss      # Include to get all modules
|   |-- _grids.scss       # grids
|   ...
|
|-- modules/              # Common modules
|   |-- _modules.scss     # Include to get all modules
|   |-- _buttons.scss     # buttons
|   |-- _utility.scss     # Module name
|   |-- _colors.scss      # Etc...
|   ...
|
|-- other/                # Random things that don't fit above
|   |-- _figures.scss     # figures
|   ...
|
|-- shame/                # Anything that needs refactoring before being put in
|   |-- _shame.scss       # The bad code
|   ...
|
`-- style.scss            # primary Sass file





/*------------------------------------*
    #VENDORS
 *------------------------------------*/
Vendor CSS found at //vendor/assets/stylesheets

|-- vendor/               # CSS or Sass from other projects
|   |-- _colorpicker.scss
|   |-- _jquery.ui.core.scss
|   ...

Includes:
[Add] normalize.css
bootstrap
[Delete] freshui
backgrid
cropper
jcarousel
lightbox
ngprogress
perfect-scrollbar
select2





/*------------------------------------*
    #RULES
 *------------------------------------*/

Use data-ui-component to describe the element so the class can remain OOCSS
/* <ul class="ui-list" data-ui-component="users-list"> */
-- csswizardry.com/2014/03/naming-ui-components-in-oocss/
