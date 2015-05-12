The `.licenserc` Specification
==============================
The `.licenserc` file format allows developers to define rules about the kinds of open-source software they can use in software projects. Software package managers, audit programs, and other developer tools can read and understand `.licenserc` files, then help developers follow the rules they set.

Whether strong personal conviction, company policy, or the terms of a business deal make licensing important, `.licenserc` can make it easier to respect the license terms others have chosen and ensure rights in your own work are clear.

What Does a `.licenserc` File Look Like?
----------------------------------------
Here is a `.licenserc` file that allows copying of software licensed under either the [MIT License][MIT] or [version 3 of the GNU Public License][GPL-3.0], linking of software licensed under the MIT License or [version 2.0 of the Apache License][Apache-2.0], and modification of MIT-licensed software:

    copy: (MIT OR GPL-3.0)
    link: (MIT OR Apache-2.0)
    modify: MIT

Where Do `.licenserc` Files Belong?
-----------------------------------
Software programs look for files named `.licenserc` starting in the current directory. If the current directory doesn't have such a file, the search continues in the current director's parent, its parent, and so on.

File Format Details
-------------------
Each line of a `.licenserc` file is either a blank line, a comment line, or a rule line.

Blank lines are empty or contain only whitespace. Comment lines begin with `#`. Software ignores both blank lines and comment lines.

Rule lines contain a use keyword followed by `:` and a valid [Software Package Data Exchange (SPDX) version 2.0 license expression][SPDX]. The license expression shows which open-source licenses can apply to software used in that way within the project. If there more than one rule line uses the same use keyword, only the last such rule line applies. If there isn't a rule line for a use keyword, any kind of open-source software can be used in that way.

Uses and Use Keywords
---------------------
`.licenserc` files may describe different rules for open-source software, depending on how that software is used in the project. Use keywords generalize different software use cases. Though the following sections include concrete examples, those examples are subject to change, and are meant only to give a general idea of what each type of use entails. Users and software projects should interpret the use keywords for themselves, in the context of specific technologies.

If a `.licenserc` file is used for compliance with law, regulation, or the terms of a contract, consult an attorney. The meaning of each use keyword may be just as important as the choice of permitted licenses for achieving legal goals.

### Copy
`copy` denotes rules about what kinds of open-source software a project can copy.

For example, a [Node.js][Node.js] project with the following `.licenserc` file...

    use: MIT

...could, as of this writing, copy [CoffeScript][CoffeeScript] into its directory and use its `coffee` command in build scripts.

### Link
`link` denotes rules about what kinds of open-source software a project can link, import, or bundle.

For example, a [Ruby][Ruby] project with the following `.licenserc` file...

    use: Ruby
    link: MIT

...could, as of this writing, install [Nokogiri][Nokogiri] and `require 'nokogiri'` in its own code.

### Modify
`modify` denotes rules about what kinds of open-source software a project can patch, statically or [dynamically][monkey patch], or otherwise alter.

For example, a [Java][Java] project with the following `.licenserc` file...

    use: GPL-2.0 WITH Classpath-exception-2.0
    modify: Apache-2.0

...could, as of this writing, copy the source code of [PDFBox][PDFBox] and apply a custom patch to add new functionality.

### Distribute
`distribute` denotes rules about what kinds of open-source software a project can distribute to users together with original code.

For example, a [Python][Python] project with the following `.licenserc` file...

    use: Python-2.0
    distribute: MIT

...could, as of this writing, bundle a copy of the [s3 module][python-s3] with its own source code for distribution to users.

Reference Implementation
------------------------
A [JavaScript reference implementation][licenserc.js] is available.

License
-------
This specification is licensed under the terms of [the Creative Commons Attribution 4.0 International Public License (CC-BY-4.0)][CC-BY-4.0]. It is the work of [K.E. Mitchell][author] and [fellow contributors][contributors].

[Apache-2.0]: http://spdx.org/licenses/Apache-2.0

[author]: http://kemitchell.com

[CC-BY-4.0]: http://spdx.org/licenses/CC-BY-4.0

[CoffeeScript]: http://coffeescript.org

[contributors]: https://github.com/licenserc/licenserc-specification/graphs/contributors

[GPL-3.0]: http://spdx.org/licenses/GPL-3.0

[Java]: http://en.wikipedia.org/wiki/Java_%28programming_language%29

[licenserc.js]: https://github.com/licenserc/licenserc.js

[monkey patch]: http://en.wikipedia.org/wiki/Monkey_patch

[MIT]: http://spdx.org/licenses/MIT

[Node.js]: https://nodejs.org

[Nokogiri]: http://www.nokogiri.org

[PDFBox]: https://pdfbox.apache.org

[Python]: https://www.python.org

[Ruby]: https://www.ruby-lang.org

[SPDX]: http://spdx.org/SPDX-specifications/spdx-version-2.0

[s3-python]: https://pypi.python.org/pypi/s3/
