The Javascript for finishline.com marks up its scripts using [JSDoc3](http://usejsdoc.org/) syntax. The documentation is automatically generated with each build of stage.finishline.com and resides at http://jsdocs.finishline.com so that developers have easy access to it.

The default JSDoc template is fairly bland, so a custom template using the marvelous [Bootstrap](http://getbootstrap.com/) library was created.

The default template for JSDoc 3 uses: [the Taffy Database library](http://taffydb.com/) and the [Underscore Template library](http://documentcloud.github.com/underscore/#template).


Installation
============

To generate documentation locally (say, to validate JSDoc comments in a dev's current branch), JSDoc3 must be installed on the dev's local machine. JSDoc3 can be installed in two different ways:


via homebrew (recommended for Mac OS X machines)
------------------------------------------------
1. Open your Terminal.
2. Update homebrew:
    * `$ brew update`
3. Make sure you have the `versions` functionality installed/enabled:
    * `$ brew tap homebrew/versions`
4. Install JSDoc3:
    * `$ brew install jsdoc3`
    * Current version at the time of this writing is *3.2.2*



via npm (must use this for Windows)
-----------------------------------
`npm` is Node's package manager.
