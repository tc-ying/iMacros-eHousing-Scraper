# e-Housing Scraper in iMacros

![hong-kong](https://github.com/tc-ying/imacros-ehousing-scraper/blob/master/docs/hkha-logo.png)

Macros to download files or HTML pages from [e-Housing](https://ehousing.housingauthority.gov.hk). They are implemented in [iMacros](https://imacros.net/).

 1. A Macro lands on a specific page.
 2. It traces HTML elements to locate target files or pages.
 3. Tweak parameters. Some of them are hard-coded.
 4. Run in browser or batch jobs.

Not the most scalable solution, these Macros are still faster than pulling data by hand. It is good enough for scheduled data refresh. **It's super fast to add or change Macros**.

![imacros](https://github.com/tc-ying/imacros-ehousing-scraper/blob/master/docs/imacros-teaser.png)

Installation
---------------
First, install [iMacros browser add-on](https://addons.mozilla.org/en-US/firefox/addon/imacros-for-firefox/). Firefox is most recommended. See installation, config and how-to-use instructions in [official page](http://wiki.imacros.net/iMacros_for_Firefox).

Find the working folder where iMacros is storing your custom macros. On Windows it's `~/Documents/iMacros/Macros` by default. Download the Macros there :

    # Change directory to working folder
    $ cd ~/Documents/iMacros
    # Clone this repository into working folder
    $ git clone https://github.com/tc-ying/imacros-ehousing-scraper Macros

I tested the Macros on Firefox version 47.0 and iMacros version 8.9.7.

Usage
---------------
In batch mode, use `Init Login.iim` to login into e-Housing system first :

    $ ./firefox imacros://run/?m=FLBWMASS%5CInit%20Login.iim &
    $ sleep 10s

User name and password is not coded inside the Macro. Configure Firefox to remember logins and passwords for e-Housing, once and for all.

Tweak parameters once in a while. Sometimes they could be search query parameters :

    # Therefore update this monthly
    SET myPERIOD 201711

Or for-loop conditions. You can set for-loop variables via iMacros UI, special variables, or simply fix them in code :

    SET !LOOP 1
    SET !VAR1 {{!LOOP}}
    ADD !VAR1 {{!VAR1}}
    ADD !VAR1 -1

File paths and file names are also subject to change :

    SET Destination \\machine\dir
    ONDOWNLOAD FOLDER={{Destination}} FILE={{File}}.pdf WAIT=YES
    
License
---------------
[![License: MPL 2.0](https://img.shields.io/badge/License-MPL%202.0-brightgreen.svg)](https://opensource.org/licenses/MPL-2.0)

This project is licensed under Mozilla Public License, Version 2.0. See LICENSE for full license text.

**Disclaimer : Contributors have agreed to submit no sensitive information to this repository for any purpose.**
