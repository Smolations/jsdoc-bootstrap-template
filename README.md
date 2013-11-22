The Javascript for finishline.com marks up its scripts using [JSDoc3](http://usejsdoc.org/) syntax. The documentation is automatically generated with each build of stage.finishline.com and resides at http://jsdocs.finishline.com so that developers have easy access to it.

The default JSDoc template is fairly bland, so a custom template using the marvelous [Bootstrap](http://getbootstrap.com/) library was created.

The default template for JSDoc 3 uses: [the Taffy Database library](http://taffydb.com/) and the [Underscore Template library](http://documentcloud.github.com/underscore/#template).


Installation
============

To generate documentation locally (say, to validate JSDoc comments in a dev's current branch), JSDoc3 must be installed on the dev's local machine. JSDoc3 can be installed in two different ways:

First, make sure you clone this repo into the proper location:

    :::bash
    # should be alongside other FINL projects (repos)
    $ cd "$workspace_path"
    $ git clone git@bitbucket.org:finishline/jsdoc-rendering-template.git

Now you're ready to install JSDoc and import the template.


via homebrew (recommended for Mac OS X machines)
------------------------------------------------
Open your Terminal and do the following:

    :::bash
    # update homebrew
    $ brew update

    # make sure you have the `versions` functionality installed/enabled
    $ brew tap homebrew/versions

    # install JSDoc3. current version at the time of this writing is 3.2.2.
    $ brew install jsdoc3

    # tell homebrew NOT to update this module when the author updates the
    # version. this ensures compatibility.
    $ brew pin jsdoc3

Homebrew installs software (by default) in /usr/local/Cellar. The template contents defined in this repository must live inside of the JSDoc install directory. In order to keep the template repo more visible and accessible, it is recommended that you create a symlink from the repo into the JSDoc templates folder:

    :::bash
    # now we can create the symlink (-s option means symlink or "soft" link)
    # $ ln -s <existing> <symlink_destination>
    $ ln -s "${workspace_path}jsdoc-rendering-template" /usr/local/Cellar/jsdoc3/3.2.2/libexec/templates/finl

    # make sure the template folder is symlinked as **finl**!


via npm (**must** use this for Windows, but works with other platforms too)
---------------------------------------------------------------------------
`npm` is Node's package manager. We generally prefer to use `npm` only when a package can ONLY be installed via `npm` (like LESS and JSHint).

1. Install JSDoc (globally). Its dependencies will be installed automatically:
    * `npm install -g jsdoc@3.2.2`

Unfortunately, `npm` doesn't have the same "pin" mechanism that homebrew has to lock down the version. Therefore, try to **never** run only `$ npm update` as it will update any modules which have been upgraded. Instead, only update specific modules which require it by specifying the module on the command line (e.g.): `$ npm update -g bless`

Depending on your operating system, the location of the global Node modules will vary. Since FINL devs are using OS X or Windows, I'll focus on those two. You can find this information out if your un `$ npm list -g` (note that the node_modules folder is omitted from the output, but each module is located within that folder). Please verify before moving forward:
- Mac OS X:  `/usr/local/lib/node_modules`
- Windows:  `~/AppData/Roaming/npm/node_modules`

In Windows, symlinking isn't as straight forward. However, we want to keep the repo in a separate location, so it's beneficial.

1. Open the Start menu and type "cmd" if your version permits, or navigate to All Programs -> Accessories -> Command Prompt. DON'T CLICK YET!
2. Right-Click on the program and select "Run As Administrator"
3. To get the paths just right, you should use a text editor to alter the paths. Since we're using cmd.exe, we must use Windows commands/paths. Below is an example of the most common usage(> replaces $ for Windows):
    * `> mklink /d "C:\Users\abc\AppData\Roaming\npm\node_modules\jsdoc\templates\finl" "D:\Development\workspaces\mac_helios_workspace\jsdoc-rendering-template"`

You can verify that the symlink worked by using Windows Explorer and navigating to the JSDoc templates directory. There should be a shortcut named "finl" that should "contain" the files in this repo.


Usage
=====

Now that everything is installed and linked, we can start generating the docs. Firstly, you should know that the file `jsdoc.conf.json` has already been committed to the [finishline](https://bitbucket.org/finishline/finish-line-main/src/101082196bcbf88ab71eb1ef5fa86fde5dfac124/modules/base/j2ee-apps/base/web-app.war/jsdoc.conf.json?at=master) project. Furthermore, the output directory of the docs (`../web-app.war/docs`) has already been added to the project's `.gitignore` file so that you can generate over and over again without needing to worry about committing any of the documentation stuff. **Careful!** If you make changes to the `jsdoc.conf.json` file, it will affect all members on the team, so be sure to communicate your changes before committing them.

An [FLGitscripts](https://bitbucket.org/finishline/flgitscripts/src/45a4d70dff5b9be4a985fdf69b2cd07172117fd7/bash_scripts/build_jsdocs.sh?at=master) command has been created to generate the documentation for you. It relies on the aforementioned configuration file, but can be run from any directory.

    :::bash
    $ buildjsdocs

Once the HTML has been generated, simply pop open any HTML file in that directory and your browser should display it. All HTML documents are linked relatively, so no web server is required to view the docs.


Conclusion
==========
Be sure to keep the JSDoc documentation handy while writing your comments! Happy commenting!
