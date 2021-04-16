# Atoms to Astronauts

> This is a landing page for a forthcoming Shopify store for Atoms to Astronauts, who sell beautifully made, eco conscious gifts that celebrate the STEM fields.

View the site at atomstoastronauts.com

## Contents

- [Screenshots](#Screenshots)
- [Features](#Features)
- [License](#License)

---

## Screenshots

![Atoms to Astronauts desktop screenshot](https://raw.githubusercontent.com/shard520/readme_resources/main/AtomsToAstronauts/desktop_view.jpg)

<p align="center">
<img src="https://raw.githubusercontent.com/shard520/readme_resources/main/AtomsToAstronauts/mobile_view.png" alt="Atoms to Astronauts mobile screenshot" width="250px">
</p>

---

## Features

The logo and social icons are in webp format with png fallback. For the logo, art-direction switching was needed to display a portrait version of the logo.

To provide both webp with png fallback support and art-direction switching with support for all screen sizes and devices the following code was needed

```html
<picture class="logo__container">
  <source
    media="(min-width: 40.625em)"
    class="logo__img"
    srcset="/img/logo/AtA_logo_landscape_W_and_G.webp"
    type="image/webp"
  />
  <source
    class="logo__img"
    srcset="/img/logo/AtA_logo_portrait_W_and_G.webp"
    type="image/webp"
  />
  <source
    media="(max-width: 650px)"
    class="logo__img"
    srcset="/img/logo/AtA_logo_portrait_W_and_G.png"
    type="image/png"
  />
  <img
    src="/img/logo/AtA_logo_landscape_W_and_G.png"
    alt="Atoms to Astronauts Logo"
    class="logo__img"
  />
</picture>
```

Note the media query to display the landscape webp image uses min-width and the em unit, but to successfully switch to the portrait logo in Safari the media query needed to be max-width with pixels.

---

The signup form has labels which are hidden when placeholder text is shown, when the user types into the fields the labels pop up to appear above the field. This is done with the following SCSS:

```scss
&__label {
  transform: translateY(-4.5rem);
  margin-top: -4.5rem;
  transition: opacity 0.2s, transform 0.2s;
  will-change: transform;
}

&__input:placeholder-shown + &__label {
  opacity: 0; // hide labels when placeholder text is visible
  visibility: hidden;
  transform: translateY(0rem);
}
```

This technique requires the labels to be written after the input in the HTML to use the adjacent sibling selector, despite the labels appearing before the input when rendered. The negative margin combined with negative translateY avoids the element occupying its normal space which would result in a blank space underneath the input when the element is hidden, and also allows the label to be positioned above the input.

---

Webp support for background images is detected via [Modernizr](https://modernizr.com/) with separate classes and declaration blocks for webp and jpg fallbacks.

---

## License

Code is licensed under the [MIT License](https://opensource.org/licenses/mit-license.php)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Atoms to Astronauts logo images are &copy; Atoms to Astronauts

Social media icons are &copy; their respective companies

Open Sans font is licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.txt)

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
