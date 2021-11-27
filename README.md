# SCSS Structure Boilerplate

SCSS Directories
------
1. Base

    > The base directory contains styles that help start a project. It depends on each project that you style accordingly.

    * **Reset:** Reset is used to normalize browser's default styles, we have 2 ways to use it:
      1. With node_modules (recommeded)
          - `@import '~normalize.css/normalize.css';`
      2. Without node_modules
          - Use current reset CSS in `base/reset.scss`
    * **Fonts:** Declaring `@font-face` to this file. See example:

      ```
        @font-face {
          font-family: 'Roboto';
          src: url(roboto.ttf);
        }
      ```

    * **Variables:** Declaring Variables
    * **Mixins:** Declaring Mixins
    * **Extends:** Declaring Extends, we should use `%` to declare the extend. See example:

      ```
        %clr {
          &::after {
            display: block;
            content: '';
            clear: both;
          }
        }
      ```

    * **Base:** Set the default style for each element in your site. See example:

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

2. Atoms
    > Atoms are the basic building blocks of matter. Applied to web interfaces, atoms are our HTML tags, such as a form label, an input or a button.

    [Readmore from Atomic Design](https://bradfrost.com/blog/post/atomic-web-design/#atoms)

3. Molecules
    > Things start getting more interesting and tangible when we start combining `atoms` together. Molecules are groups of `atoms` bonded together and are the smallest fundamental units of a compound. These molecules take on their own properties and serve as the backbone of our design systems.

    [Readmore from Atomic Design](https://bradfrost.com/blog/post/atomic-web-design/#molecules)

4. Organisms
    > Molecules give us some building blocks to work with, and we can now combine them together to form organisms. Organisms are groups of molecules joined together to form a relatively complex, distinct section of an interface.

    [Readmore from Atomic Design](https://bradfrost.com/blog/post/atomic-web-design/#organisms)

5. Layout

    > The layout directory contains styles that are large containers of a page.

    * **Grid:** Create the column.
    * **Layout:** Creating layout have 2 columns with sidebar left or right. See example:

      ```
        .layout-2-col-left {
          display: flex;
          > .col-left {
            width: 32%;
          }
          > .col-main {
            width: 68%;
          }
        }
      ```

6. Utilities
  
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

7. Pages
    
    > The pages directory contains any specific styles that a page may need to change from the generic layout or modules.


> **Notice:** In each subfolder have 1 file `_all.scss` this is the place for you `@import` all file have the same level as it. And all file `_all.scss` will be imported to root file `styles.scss`


Rules
------
  * In case add more file please import correctly directory
  * Avoid nesting too many levels
  * Break files out into small modules
  * Avoid using many `!important`
  * Place media queries to the end of each file

Compiler
------
  * Quick compile with node-sass: 
      ```
        npx node-sass -w -o ./ scss/styles.scss
      ```
    
  * In case setup for the large project, we should use [webpack](https://webpack.js.org/) or [gulp](https://gulpjs.com/).

