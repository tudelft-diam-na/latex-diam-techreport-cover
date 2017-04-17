diamtrcov
=========

The `diamtrcov` latex package automatically adds cover pages for a DIAM
technical report, independent of the document class used for the report, font
changes or custom geometry definitions.  It is sufficient to add

    \usepackage[number=17-01,year=2017]{diamtrcov}

to the preamble of your latex document with the title and authors specified via
`\title` and `\author`.  The values `17-01` and `2017` serve as an example.

Package options
---------------

The package takes the following options:

*   `number=<NUMBER>` (mandatory)

    Set the number of the technical report to `<NUMBER>`, e.g. `number=17-01`.

*   `year=<YEAR>` (mandatory)

    Set the year of publication to `<YEAR>`, e.g. `year=2017`.

*   `auto` (default)

    Automatically create the cover at the beginning of the document.

*   `noauto`

    Do not automatically create the cover.  Use `\diamtrcover` at any point in
    the document to create the cover at that position.

The options should be specified via `\usepackage` as follows:

    \usepackage[number=17-01,year=2017]{diamtrcov}

Commands
--------

The title and the authors of the technical report should be defined by
`\title` and `\author` or `\diamtrcovtitle` and `\diamtrcovauthor`.  The
`\diamtrcov...` versions have precedence.

When the option `noauto` is passed to the package the cover can be generated
at any point in the document by calling `\makediamtrcov`.

Examples
--------

Simplest example with automatic cover pages:

    \documentclass[a4paper]{article}
    \usepackage[number=17-01,year=2017]{diamtrcov}
    \title{Title of the report}
    \author{Authors}
    \begin{document}
        ...
    \end{document}

Manual version:

    \documentclass[a4paper]{article}
    \usepackage[number=17-01,year=2017,noauto]{diamtrcov}
    \title{Title of the report}
    \author{Authors}
    \begin{document}
        \makediamtrcov
        ...
    \end{document}

You can change the font of your document without affecting the appearance of
the cover pages.  Furthermore, you can use `\maketitle` to add the title and
authors after the cover pages, for example with affiliations.  The command
`\thanks` is disabled in the cover pages.  Example:

    \documentclass[a4paper]{report}
    \usepackage[number=17-01,year=2017]{diamtrcov}
    \usepackage{cmbright}
    \usepackage[T1]{fontenc}
    \title{Title of the report}
    \author{Author1\thanks{DIAM TU Delft}\and Author2}
    \begin{document}
        \maketitle
        ...
    \end{document}

If necessary you can specify an alternative title and authors for the cover
pages via the `\diamtrcovtitle` and `\diamtrcovauthor` commands, e.g. to
control line breaks for both the cover pages and the titlepage of the document
class.  Example:

    \documentclass[a4paper]{article}
    \usepackage[number=17-01,year=2017]{diamtrcov}
    \title{Title}
    \diamtrcovtitle{Cover title}
    \author{Author1\thanks{DIAM TU Delft}\and Author2}
    \diamtrcovauthor{AuthorX\and AuthorY}
    \begin{document}
        % Cover page shows 'Cover title' and 'AuthorX and AuthorY'
        \maketitle % shows 'Title' and 'Author1^* and Author2'
        ...
    \end{document}
