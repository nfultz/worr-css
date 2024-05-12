# worr-css: Easier Warnier-Orr diagrams in HTML

## Features

1. Sequence
2. Repitition
3. Alternation
4. Negation
5. Noop



## What didn't work

Nested Curly braces were a pain:

* ChatGPT initially recommended
    ```
    // Get the length of the list
    const listLength = document.querySelectorAll('ul li').length;
    // Adjust the font-size of the curly brace based on the length of the list
    document.querySelector('ul::before').style.fontSize = `${listLength * 16}px`;
    ```

    This does not work because the DOM can't query psuedo-elements like `::before`.
* It next suggested:
    ```
    ul::before {
      content: '{';
      font-size: calc(16px + 5px * (counter(my-counter))); /* Calculate font size based on counter */
      display: inline-block;
      margin-right: 5px;
    }
    ul li {
      counter-increment: my-counter; /* Increment counter for each list item */
    }
    ```

    This does not work, browsers do not support `counter` within font-size.

* Setting one large background image on `ul::before`
  * many sizing issues, need to specify number of rows for `scale()` transformation.
* Setting several background images on `ul::before`
  * many sizing issues, no good way to position corner of the curly brace.
* Setting several background images on `ul li:first-child()` etc
  * No way to specifiy inner-corner.
  * Often led to gaps between sections.
* Next, I came up with using border image in conjuction with an SVG data url
  of a curly brace, a la [emoji favicons](https://css-tricks.com/emoji-as-a-favicon/).
  * That workded, but was ugly
* Finally, I replaced that with a full SVG of a pair of `{}`, which came out better.
* This was combined with `flex` layout, center-aligned to get it lined up correctly.

