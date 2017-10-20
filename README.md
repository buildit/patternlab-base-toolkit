# PatternLab Base Toolkit

## Overview

This is an improved version of [PatternLab Node Edition Gulp](https://github.com/pattern-lab/edition-node-gulp) with SASS compilatian included.

Check out the [Technical Bits](#technical-bits) if you want to learn more about it.

## Installation

Clone the current repo:

    $ git clone git@bitbucket.org:digitalrigbitbucketteam/patternlab-base-toolkit.git
    $ cd patternlab-base-toolkit

Install all the dependencies:

    $ npm install

Load the starterkits, if any, for instance:

    $ gulp patternlab:loadstarterkit --kit=starterkit-mustache-demo

Run the project:

    $ npm start

You can now access the website at <http://localhost:3000>.

## Technical bits

There are some major differences from the original project, namely:

- SASS compilation
- Directory structure
- Improved code standards to be used throughout the project

### SASS compilation

The `gulpfile.js` will automatically compile, inject, and reload the browser upon changes to any of the `*.scss` files available in the directory `/source/sass/`.

# TODO

- [ ] Add support for autoprefixer when compiling SCSS files.
- [ ] Add support for normalize
- [ ] Add support for automatic SASS linting via stylelint.
