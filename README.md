# Sass Accoutrement

[![Build Status](https://travis-ci.com/oddbird/accoutrement.svg?branch=main)](https://travis-ci.com/oddbird/accoutrement)

**Robust design systems** require
_meaningful_, _readable_, _reusable_ code.
These Sass utilities are designed to
help define and manage your design tokens
(colors, fonts, sizes, etc.)
in a format that can be understood
by both humans and parsers --
opening the door for automation,
while improving consistency and readability.
These tools also integrate with [Herman][herman],
our automated living pattern-library generator
built on [SassDoc][sassdoc].

[herman]: https://www.oddbird.net/herman/
[sassdoc]: http://sassdoc.com/

- [Official Site](https://www.oddbird.net/accoutrement/)
- [Documentation](https://www.oddbird.net/accoutrement/docs/)
- [Source Code](https://github.com/oddbird/accoutrement/)
- [Issues](https://github.com/oddbird/accoutrement/issues)

_Brought to you by [OddBird][oddbird] --
the creators of [Susy][susy],
[True][true],
and [Herman][herman]._

[oddbird]: https://www.oddbird.net/
[susy]: https://www.oddbird.net/susy/
[true]: https://www.oddbird.net/true
[herman]: https://www.oddbird.net/herman
[fonts]: https://www.oddbird.net/accoutrement/docs/type.html

## Installation

Install the package with npm or yarn

```bash
npm install accoutrement [--save-dev]
yarn add accoutrement [--dev]
```

Use what you need:

```scss
// all the modules (these are functionally the same)
@use "<path-to>/accoutrement";
@use "<path-to>/accoutrement/sass/tools";

// individual modules (at `/accoutrement/sass/<name>`)
@use "<path-to>/accoutrement/sass/color";
```

If you're using [Eyeglass](https://github.com/linkedin/eyeglass),
you can use the default "tools" (core + plugins) using only:

```scss
@use "accoutrement";
```

## Modules for common data types

- **[Animate](https://www.oddbird.net/accoutrement/docs/animate.html)** --
  For managing CSS transitions and animations
- **[Color](https://www.oddbird.net/accoutrement/docs/color.html)** --
  For managing CSS colors and contrast-ratios
- **[Scale](https://www.oddbird.net/accoutrement/docs/scale.html)** --
  For managing CSS sizes: typographic scales, spacing, etc.
- **[Type](https://www.oddbird.net/accoutrement/docs/ratios.html)** --
  For managing webfonts, generated content, and other text needs
- **[Ratios](https://www.oddbird.net/accoutrement/docs/type.html)** --
  For managing aspect and typography ratios
  (several common ratios are provided)
- **[Variables](https://www.oddbird.net/accoutrement/docs/vars.html)** --
  For converting Sass maps and variables into CSS custom properties
- **[Utilities](https://www.oddbird.net/accoutrement/docs/utils.html)** --
  For helpers with Sass lists, strings, and maps

## Tokens

The **Token** module provides
a special syntax for managing design tokens
with Sass "map" objects:

```scss
$map: (
  'root': 16px,
  'gutter': 1em,
);
```

Using the custom syntax,
we can extend maps to handle internal reference,
and functional adjustments --
capturing meaningful relationships
between design tokens:

```scss
$map: (
  'root': 16px,
  // internal reference & adjustments
  'gutter': '#root'
    (
      "scale": ('_major-third', 1),
      "convert-units": "rem",
    ),
);
```

Map storage serves a larger purpose:

- Related data is grouped explicitly,
  making the code more readable and maintainable
- The "single source of truth"
  encourages reusable design patterns
- Meaningful structure allows automation,
  from [automated style guides][herman]
  to automated functionality

[herman]: https://www.oddbird.net/herman/
[type]: https://www.oddbird.net/accoutrement/docs/type.html

This module provides the generic
(non data-specific)
setup and syntax parsing:

- Retrieve & parse map values
  with `token.get()`
  and other [token api functions][api]
- Use the many [registered functions][internal]
  to manipulate tokens in the map
- Register your own [functions][functions],
  for extra functionality

[api]: https://www.oddbird.net/accoutrement/docs/token-api.html
[internal]: https://www.oddbird.net/accoutrement/docs/token-internal.html
[functions]: https://www.oddbird.net/accoutrement/docs/token-register.html

