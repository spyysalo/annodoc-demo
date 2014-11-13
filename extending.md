---
layout: base
title:  'Extending the documentation'
---

# Extending the documentation

This page provides instructions on how to extend the Universal
Dependencies documentation. These instructions are a work in progress.

(This is king of technical, and getting stuff wrong might end up
(reversibly) clobbering parts of existing documentation. Take care
when applying these instructions, and don't hesitate to ask other
developers if in doubt.)

## Adding new languages

The documentation for each language consists primarily of four
collections of pages: one providing a general overview of the
guidelines for the language, and one each for detailed guidelines for
POS, features, and relations. To add a new language to the
documentation, it is necessary to create these collections and some
supporting documentas. To make this easier, the repository has a set
of empty templates that you can copy to get started. (*Note*: do not
modify any of the templates directly, only copies of the templates.)

The language that the input documents relate to is encoded in many of
the relevant file and directory names using the two-letter [ISO 639-1
code](http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes).  In the
following, the string `LC` is used as a placeholder for the language
code. When following these instructions, replace `LC` with the
appropriate language code (in lowercase) so that e.g. for Swedish
`_sv_pos/` is used instead of `_LC_pos/`.

* Create a copy of each template collection:
`LC` with your language code):

    for c in overview pos feat dep; do cp -r _template-$c _LC-$c; done

* Create copies of HTML tables summarizing the POS tags,
features, and dependencies:

    for c in pos feat dep; do cp _includes/template-${c}-table.html _includes/LC-${c}-table.html; done

* Replace all references to "template" with references to the
language code in the copied materials:

    perl -p -i -e 's/template/LC/' _LC-*/*.md

* Edit `_config.yml` to let Jekyll know about the newly created
  collections. Copy the section following the text "Template" and
  replace all occurrences of "template" in the copy with the language
  code.

* Edit `index.md` to add links to the newly created materials. This
  involves two parts:

  * First, add a line like the following in the section with the
    comment "links to per-language sections" (replacing "LANGUAGE"
    with the name of the language):

    `<li class="ui-state-default"><a href="#language-LC">LANGUAGE</a></li>`

  * Second, copy the commented-out section labeled "new tab template",
    remove the comments, and replace "LC" with the language code.

* Finally, add all of the materials just created to Git.

    git add _LC-{overview,pos,dep,feat} _includes/LC-{pos,feat,dep}-table.html index.md _config.yml
    git commit
    git push

### Notes about the implementation

The input directory structure is just one level deep (e.g. the source
document for `en/dep/nsubj` is in `en-dep/nsubj`) to allow
e.g. documents relating to English POS tags to be kept separate from
those relating to English dependencies. Jekyll allows nested
collection structure, but if e.g. English POS documents were in
`_en/pos` and English dependency documents in `_en/dep`, it would not
be possible to list the two "subcollections" separately.

The "index" and "all" documents are stored in `_LC-overview/` instead
of `_LC-pos` (etc.) to exclude them from automatically generated
listings.
