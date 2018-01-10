# PatternLab Base Toolkit

## Overview

This is an improved version of [PatternLab Node Edition Gulp](https://github.com/pattern-lab/edition-node-gulp) with SASS compilatian included.

Check out the [Technical Bits](#technical-bits) if you want to learn more about it.

## Setup and run

### Requirements

The (main) requirement for running this project is [Node](https://nodejs.org) and [NPM](https://www.npmjs.com) (which usually comes when installing Node).

The recommended way to have NPM installed is via [NVM](https://github.com/creationix/nvm#installation) which will also allow you to have different versions installed at the same time.

There's nothing wrong in using any other way to install Node, like the default system-installed Node version, as long as it's above version 5.0.

_Optionally, but not recommended_: once you have installed Node and NPM, you can install Gulp 4 globally, as follows:

    $ npm install -g gulpjs/gulp#v4.0.0

You do not need this, as you will see later.

If you're stumbling on any error, have a look at the [troubleshooting section](#Troubleshooting) below

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

# Troubleshooting

## Error: Node Sass does not yet support your current environment

When installing the starterkit you're getting an error like the following:

    Error: Node Sass does not yet support your current environment: OS X 64-bit with Unsupported runtime (59)

This seems to be related to [this (resolved) issue](https://github.com/sass/node-sass/issues/1764), and you can fix it by running the following command:

    $ npm rebuild node-sass

## I'm using the starterkit-x but can't see any styles

This would normally happen if you've installed the `starterkit-mustache-demo`, since it places both the CSS and the SASS files in the same folder `/source/css/`.

Following is a _quick and dirty_ solution if you just need to get things working.  If you want a proper solution, read further.

Add the following line at the bottom of the `/source/sass/style.scss` file:

```scss
@include '../css/style.scss';
```

That should be enough to do the trick.

If you want a _proper_ solution, you'll have to move the sass files in the right location.
In order to do that, the following steps are necessary:

1. Copy all the folders and their contents from `/source/css/scss/` into `/source/sass/`.
2. Move `/source/css/style.scss` to `/sources/sass/style.scss`, overriding the previous file.
3. Edit the file `/srouces/sass/style.scss` and remove the `scss/` portion from any included path.

# TODO

- [x] Add support for autoprefixer when compiling SCSS files.
- [x] Add support for normalize
- [x] Add support for automatic SASS linting via stylelint.
- [ ] Test in conjunction with official starterkits
- [ ] Fix stylelint config against BEM class names
