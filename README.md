# vue-simple-icons

[Simple Icons](https://simpleicons.org/) as Vue components.

## Install

```bash
yarn add vue-simple-icons
```

## Usage

```js
import { FacebookIcon, TwitterIcon, ... } from 'vue-simple-icons'
```

See all icons and usage here: https://vue-simple-icons.mainvest.com

### Sizing

By default, icons will be sized based on the font size of the parent element.

You can set a custom size using the `size` attribute.
For multiple based sizing, pass the desired multiple followed by an `x`.

```html
<facebook-icon size="1.5x" class="custom-class"></facebook-icon>
```

You can also set a `px` size directly by passing an integer

```html
<facebook-icon size="25" class="custom-class"></facebook-icon>
```

## Note
* Because [identifiers can’t start with numeric literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Identifier_after_number), names beginning with numbers have them converted to English words. For example, the logo for 500px is available as `FiveHundredPxIcon`.
* Versioning follows the [Simple Icons](https://github.com/simple-icons/simple-icons) package.

## Credit

Based on [**vue-feather-icons**](https://github.com/egoist/vue-feather-icons) by [egoist](https://github.com/egoist)

## Upgrade Instructions

* `npm i simple-icons`
* `npm version [latest version of simple-icons]`
* `npm publish`
* `git add .`
* `git commit -m "Release [latest version of simple-icons]"`
* `git push`