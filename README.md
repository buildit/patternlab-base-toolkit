# PatternLab Base Toolkit

## Overview

This is merely just an attempt in a modular and reusable Design System using PatternLab.

This project is based on [PatternLab Node Edition Gulp](https://github.com/pattern-lab/edition-node-gulp).

Check out the [Technical Bits](#technical-bits) if you want to learn more about it.

## Design System

Based on different ideas and methodologies, I've tried to aim for something that is as comprehensive and clear as possible, which means that the following sections are currently covered (although most of the them are mostly a reference and need to be filled in appropriately):

1. **Principles**: this can be summarised as the most important part of the Design System, it should cover areas like _personality_, _writing style_, _colours_, _illustrations_, _typography_, with simple and direct information on the principles behind each of them.
2. **Core**: this section includes more technical aspects, also considered the _foundation_ of the whole system, this includes areas like _illustrations_, _iconography_, _colours_ and their usage, _typography_. It can be also accompained with downloadable resources to be used in various media (emails, social media, ...).
3. **Components**: this section is what comes out of the above two points: it's essentially a pattern library that should feature elements that have been created.
4. **Applications**: this section covers practical examples of applications of the various components, possibly used as a way to document and test them.

The current implementation provides only a scheleton for this, moreover the various bits are going to be provided as separate dependencies that can be extended and improved or replaced as needed.

## Technical bits

There are some major differences from the original project, namely:

- SASS compilation
- Directory structure
- Improved code standards to be used throughout the project

### SASS compilation

The `gulpfile.js` will automatically compile, inject, and reload the browser upon changes to any of the `*.scss` files available in the directory `/source/sass/`.

It comes with the following dependencies:

- [Eyeglass](http://eyeglass.rocks/) for enhanced npm module loading within the CSS.
- [Normalize-scss](https://github.com/JohnAlbin/normalize-scss) as a SCSS module for Normalize.css .
- [Bourbon-Neat](http://neat.bourbon.io/) for the grid system.
- [Modularscale-sass](https://github.com/modularscale/modularscale-sass) for typography following [Modular Scale](http://modularscale.com) principles.
- [Typi](https://github.com/zellwk/typi) for responsive typography and vertical rhythm.

**NOTE** apparently there's a bug in Modularscale-sass that breaks compatibility with the latest version of Eyeglass, a [bug report has been opened](https://github.com/modularscale/modularscale-sass/issues/141), in the meantime you would need to change the `eyeglass` configuration object in the `package.json` found in `/node_modules/modularscale-sass/`:

    "eyeglass": {
      "exports": "eyeglass-exports.js",
      "name": "modularscale",
      "needs": "^1.2.1"
    }

# TODO

- Add support for autoprefixer when compiling SCSS files.
