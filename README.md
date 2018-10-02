# SCSS Structure Boilerplate

SCSS Directories
------
1. Base

    > The base directory contains styles that help start a project. It depends on each project that you style accordingly.

    * **Reset:** Reset CSS for all browser, I have put the code in this file and add it to top of @import, because of it only for reset, please don't use variables, mixin... here. If you want to set the default style for each element please go to `_base.scss`.
    * **Fonts:** Declaring `@font-face` to this file. See example:

      ```
        @font-face {
          font-family: 'Roboto';
          src: url(roboto.ttf);
        }
      ```

    * **Variables:** Declaring Variables
    * **Mixins:** Declaring Mixins
    * **Extends:** Declaring Extends, You should use `%` to declare the extend. See example:

      ```
        %clr {
          &::after {
            display: block;
            content: '';
            clear: both;
          }
        }
      ```

    * **Base:** This file is the place for you set the default style for each element in your site. See example:

      ```
        body {
          font-size: 14px;
        }
        a {
          color: #666;
          &:hover {
            color: #000;
          }
        }
        h1 {
          font-size: 40px;
        }
        h2 {
          font-size: 36px;
        }
        ...
      ```

2. Layout

    > The layout directory contains styles that are large containers of a page.

    * **Grid:** Create the column, It depends in your project.
    * **Layout:** Usually, using for creating layout have 2 column with sidebar left or right and consist site container. See example:

      ```
        .container {
          max-width: 1200px;
          padding: 0 15px;
          margin: 0 auto;
        }
        .layout-2-col-left {
          @extend %clr;
          > .col-left {
            width: 32%;
            float: left;
          }
          > .col-main {
            width: 68%;
            float: right;
          }
        }
      ```

    * **Header:** Style for site header
    * **Footer:** Style for site footer

3. Modules
  
    > A page may consist of multiple modules and should be styled individually. We usually use it to create the style for form, btn... or other modules. See example:

    ```
      // Button file
      .btn {
        padding: 10px 20px;
        border-radius: 3px;
        font-size: 16px;
        background: #000;
      }

      // Form file
      input:not([type="checkbox"]):not([type="radio"]) {
        width: 100%;
        border: 1px solid #e1e1e1;
        height: 32px;
        border-radius: 3px;
        padding: 0 15px;
        font-size: 16px;
      }
    ```

4. Pages
    
    > The pages directory contains any specific styles that a page may need to change from the generic layout or modules.

5. State

    > A state is something that augments and overrides all other styles. States should be made to stand alone and are usually built of a single class selector. See example:

    ```
      .is-hidden {
        display: none !important;
      }
      .is-active {
        display: block !important;
      }
    ```


> **Notice:** In each subfolder have 1 file `_all.scss` this is the place for you `@import` all file have the same level as it. And all file `_all.scss` will be imported to root file `styles.scss`


Rules
------
  * In case add more file please import correctly directory
  * Avoid code too many levels
  * Break files out into small modules
  * Avoid using many `!important`, except file `_state.scss`
  * Put media queries to the end of each file

Compiler
------
  * Quick compile with node-sass: 
      ```
        node-sass -w -o ./ scss/styles.scss
      ```
    
  * In case setup for the large project, you should use [webpack](https://webpack.js.org/) or [gulp](https://gulpjs.com/).

