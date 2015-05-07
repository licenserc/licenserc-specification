The `.licenserc` Specification
===========================

What is `.licenserc`?
------------------
licenserc helps developers define and follow rules about the kinds of open-source software they can use in software projects. `.licenserc` is a file format for describing those rules that software package managers, audit programs, and other developer tools can understand.

Whether strong personal conviction, company policy, or the terms of a business deal make licensing important, `.licenserc` can make it easier to respect the license terms others have chosen and ensure rights in your own work are clear.

What Does a `.licenserc` File Look Like?
------------------------------------
Here is a `.licenserc` file that allows copying of software licensed under either the [MIT License][MIT] or [version 3.0 of the GNU Public License][GPL-3.0], linking of software licensed under the MIT License or [version 2.0 of the Apache License][Apache-2.0], and modification of MIT-licensed software:

    copy: (MIT OR GPL-3.0)
    link: (MIT OR Apache-2.0)
    modify: MIT

Where Do `.licenserc` Files Belong?
--------------------------------
Software using `.licenserc` will look for files named `.licenserc`, starting in the current directory. If the current directory doesn't have a `.licenserc` file, the software will search the parent directory, its parent directory, and so on until it finds a `.licenserc` file.

File Format Details
-------------------
Each line of a `.licenserc` file is either a blank line, a comment line, or a rule line.

Blank lines are empty or contain only whitespace. Comment lines begin with `"#"`. Both blank lines and comment lines are ignored by `.licenserc`-compatible software.

Rule lines begin with a use keyword followed by `":"` and a valid [SPDX version 2.0 license expression][SPDX]. The license expression shows what terms open-source software must be licensed under to be used in that way within the project. If a `.licenserc` has more than one rule lines for a use keyword, the last is read and the rest are ignored. If a `.licenserc` file does not have a rule line for a use keyword, any kind of open-source work can be used in that way.

Uses and Use Keywords
---------------------
licenserc files include rules for several kinds of ways that projects can utilize open-source software. These uses are generalizations that individual `.licenserc` users and technology-specific `.licenserc`-compatible software tools should interpret for specific technologies. Though the following sections include concrete examples, those examples are subject to change, and are meant only to give a general idea of what each type of use entails. If a `.licenserc` file is used for compliance with law, regulation, or the terms of a contract, consult an attorney to determine how a `.licenserc` file and related tools can be used to track compliance.

### "copy"
The "copy" use keyword denotes rules about what kinds of open-source software a project can copy.

For example, a [Node.js][Node.js] project with the following `.licenserc` file:

    use: MIT

... could, as of this writing, install [CoffeScript][CoffeeScript] as a development dependency with [npm][npm] and use the `coffee` command in build scripts.

### "link"
The "link" use keyword denotes rules about what kinds of open-source software a project can link, import, or bundle.

For example, a [Ruby][Ruby] project with the following `.licenserc` file:

    link: MIT

... could, as of this writing, install [Nokogiri][Nokogiri] from [RubyGems][RubyGems] with [Bundler][Bundler] and `require 'nokogiri'` in its own code.

### "modify"
The "modify" use keyword denotes rules about what kinds of open-source software a project can modify.

For example, a [Java][Java] project with the following `.licenserc` file:

    modify: Apache-2.0

... could, as of this writing, install [PDFBox][PDFBox] from [Maven][Maven], apply a custom patch to add new functionality.

License
-------
The `.licenserc` Specification is licensed under the terms of the Creative Commons Attribution 4.0 International Public License (SPDX [CC-BY-4.0][CC-BY-4.0]).

[Apache-2.0]: http://spdx.org/licenses/Apache-2.0

[Bundler]: http://bundler.io

[CC-BY-4.0]: http://spdx.org/licenses/CC-BY-4.0

[CoffeeScript]: http://coffeescript.org

[GPL-3.0]: http://spdx.org/licenses/GPL-3.0

[Java]: http://en.wikipedia.org/wiki/Java_%28programming_language%29

[Maven]: https://maven.apache.org

[MIT]: http://spdx.org/licenses/MIT

[Node.js]: https://nodejs.org

[Nokogiri]: http://www.nokogiri.org

[npm]: http://npmjs.com

[PDFBox]: https://pdfbox.apache.org

[Ruby]: https://www.ruby-lang.org

[RubyGems]: http://rubygems.org

[SPDX]: http://spdx.org/SPDX-specifications/spdx-version-2.0
