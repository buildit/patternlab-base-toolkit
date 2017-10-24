# PatternLab Base Toolkit

## Overview

This is an improved version of [PatternLab Node Edition Gulp](https://github.com/pattern-lab/edition-node-gulp) with SASS compilatian included.

Check out the [Technical Bits](#technical-bits) if you want to learn more about it.

## Setup and run

### Requirements

The (main) requirement for running this project is [Node](https://nodejs.org) and [NPM](https://www.npmjs.com) (which usually comes when installing Node).

The recommended way to have NPM installed is via [NVM](https://github.com/creationix/nvm#installation) which will also allow you to have different versions installed at the same time.

There's nothing wrong in using any other way to install Node, like the default system-installed Node version, as long as it's above version 5.0.

_Optionally_, once you have installed Node and NPM, you can install Gulp 4 globally, as follows:

    $ npm install -g gulpjs/gulp#4.0

You do not need this, as you will see later.

### Installation

Clone the current repo:

    $ git clone git@bitbucket.org:digitalrigbitbucketteam/patternlab-base-toolkit.git
    $ cd patternlab-base-toolkit

Install all the dependencies:

    $ npm install

Load the starterkits, if any, for instance:

    $ npm install starterkit-mustache-demo
    $ npm run gulp -- patternlab:loadstarterkit --kit=starterkit-mustache-demo

Run the project:

    $ npm start

You can now access the website at <http://localhost:3000>.

## Technical bits

There are some major differences from the original project, namely:

- SASS compilation
- Concatenation of PL styles (`pattern-scaffolding` files)
- Directory structure
- Improved code standards and linting used throughout the project

### SASS compilation

The `gulpfile.js` will automatically compile, inject, and reload the browser upon changes to any of the `*.scss` files available in the directory `/source/sass/`.

The current version now includes [normalize](https://necolas.github.io/normalize.css/), albeit [its SASS version](https://github.com/JohnAlbin/normalize-scss), and [autoprefixer](https://github.com/postcss/autoprefixer) to automate vendor prefixes.

### Concatenation of PL styles

By default PatternLab comes with some generic styles inside of `/source/css/pattern-scaffolding.css`.

This version allows you to split the CSS in multiple ones, as long as they have the string `pattern-scaffolding` within its name. The output will be called `pattern-scaffolding.css`.

This could be useful if you're buidling starter kits that inject different specific `pattern-scaffolding` files without having to override the ones injected previously.

As an example you can have in `/source/css/` the following files:

- `00-pattern-scaffolding-base.css`
- `01-pattern-scaffolding-rules.css`

Once running it would generate `pattern-scaffolding.css` that is automatically read by PatternLab.

As an example this version comes with an augmented version (compared to the original PL version) that provides some possibly useful styles.

# TODO

- [x] Add support for autoprefixer when compiling SCSS files.
- [x] Add support for normalize
- [x] Add support for automatic SASS linting via stylelint.
- [ ] Test in conjunction with official starterkits
- [ ] Fix stylelint config against BEM class names
