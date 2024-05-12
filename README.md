# worr-css: Easier Warnier-Orr diagrams in HTML


## What didn't work

* ChatGPT initially recommended
    ```
    // Get the length of the list
    const listLength = document.querySelectorAll('ul li').length;
    // Adjust the font-size of the curly brace based on the length of the list
    document.querySelector('ul::before').style.fontSize = `${listLength * 16}px`;
    ```.

    This does not work because the DOM can't query psuedo-elements like `::before`.

* Setting one large background image on `ul::before`
  * many sizing issues, need to specify number of rows for `scale()` transformation.
* Setting several background images on `ul::before`
  * many sizing issues, no good way to position corner of the curly brace.
* Setting several background images on `ul li:first-child()` etc
  * No way to specifiy inner-corner.

