# SCSS Folder Structure Boilerplate

SCSS Directory
------
1. Base
  * Reset : Reset CSS for all browser, I have put the code in this file.
  * Fonts : Declaring @font-face to this file. See the example below.
    ```
      @font-face {
        font-family: 'Roboto';
        src: url(roboto.ttf);
      }
    ```
  * Variables : Declaring Variables
  * Mixins : Declaring Mixins
  * Extends : Declaring Extends, You should use `%` to declare the extend. See the example below.
    ```
      %clr {
        &::after {
          display: block;
          content: '';
          clear: both;
        }
      }
    ```
  * Base : This file is the place for you set default CSS for your site, It depends on each project. See the example below.
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
  * Grid : Create the column, It depends in your project.
  * Layout : Using for creating layout have 2 column with sidebar left or right and consist container of the site. See example below.
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
  * Header : Style for site header
  * Footer : Style for site footer
