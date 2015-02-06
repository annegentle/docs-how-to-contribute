====================================================
Converting an existing document from Docbook to reST
====================================================

.. _docbook2rst:

These instructions help you convert a Docbook publication into a reST document for web delivery.

Converting from Docbook to reST requires three steps:

1. Clean up your Docbook.

2. Convert your docs.

3. Clean up your reST.

Clean up your Docbook
~~~~~~~~~~~~~~~~~~~~~

#. Remove cross-reference links inside of tables.

#. Remove nested markup. 

    While the conversion script translates nested XML markup into RST, Sphinx will not parse or build the RST results correctly. This is because, as of February 2015, RST doesn't support nested markup.

    .. note:: 

    Fixing RST tables manually is time-consuming. If your document contains nested RST markup inside of tables, the effort of manual clean-up increases significantly. It's better to remove all nested markup in Docbook, prior to script conversion.

#. Remove markup in tables wherever possible.

    Sphinx may not process markup correctly when broken across table rows.

    When text with inline markup breaks across lines, Sphinx parses the markup erratically. For example, Sphinx inserts a space between characters broken across lines, and may publish inline markup without parsing it.

Convert your docs
~~~~~~~~~~~~~~~~~

Create a GitHub repository
--------------------------

Create a new repository for your conversion results.

Run the conversion script
-------------------------

1. Follow the instructions for `converting Docbook to RST`_.

.. _converting Docbook to RST: https://one.rackspace.com/pages/viewpage.action?title=Notes+on+converting+DocBook+to+RST&spaceKey=~marg7175

2. Run `sphinx-quickstart` in your doc repo.

The script walks you through setup, prompting you to confirm default values or choose alternatives.

3. Accept the Sphinx defaults.

    For version number, enter the current product or document version followed by 'b'. For example::

    1.01b1

    `1.0` is the document version. 'b1' indicates that this is the first version of a document converted from an existing document. (If the document or product version remains unchanged, the next iteration's version number would be 1.0b2.)

Clean up your reST
~~~~~~~~~~~~~~~~~~

Set up your authoring environment
---------------------------------

Choose a code editor that supports RST markup. `Sublime Text`_ offers native RST support.

Follow OpenStack conventions for `authoring in RST`_.

(Note to self: make a wiki page that simplifies OpenStack conventions for RST.)

.. _authoring in RST: https://wiki.openstack.org/wiki/Documentation/Markup_conventions
.. _Sublime Text: http://www.sublimetext.com/2

Edit your index.rst file
------------------------

1. Open the `index.rst` file in the top level of your doc repo.

2. Create the navigation structure for your document.

.. note::
    The `index.rst` file serves as a table of contents and provides the structure for left-rail navigation on developer.rackspace.com.

    You can use the `index-sample.rst` file in this document's repo folder as a template.

#. If your doc has multiple volumes, list them 
    under second-level headings in the same `index.rst` file. For 
    example::

    Getting Started Guide
    ~~~~~~~~~~~~~~~~~~~~~

    GSG/gs-overview

    Developer Guide
    ~~~~~~~~~~~~~~~

    DG/dg-overview

Rename your files
-----------------

Choose meaningful names for individual doc files. For example::

    `GettingStartedGuide/api-reference`

    is better than

    `GettingStartedGuide/chapter-2`

Update `index.rst` to reflect your changes.

Clean up tables
---------------

Tables require significant manual cleanup post-conversion. 

#. Remove markup in tables whenever possible. 

#. Remove markup from text in bulleted or itemized lists. 

    RST treats markup as an unexpected termination of the list.

#. Remove cross references from tables.

    If a cross reference is necessary, replace all cross references inside a table with a single cross reference after the table. 

Repair links and cross-references
---------------------------------

Remove orphaned code
--------------------

#. Remove the following unnecessary code blocks wherever you find them::

    .. raw:: html
        <div
        class="itemizedlist"
        xmlns=""
        d="http://docbook.org/ns/docbook"
        svg="http://www.w3.org/2000/svg">

#. Remove `programlisting` and `screen` from all `.. code::` directives. 

    If Sphinx offers `Pygment support`_ for a suitable replacement, enter it instead. For example::

        Replace

        .. code:: programlisting

        with

        .. code:: bash

.. _Pygment support: http://sphinx-doc.org/markup/code.html

Test your output
----------------

#. Build HTML files from your RST source.

`Follow these steps`_.

Test your updates to RST files frequently with Sphinx's `make html` process.

.. _Follow these steps: https://one.rackspace.com/display/devdoc/Sphinx+documentation+notes+for+multi-product+user+guides






Things I did in this conversion, either seriously or to play around:


    Removed numbering to highlight that content needs to be organized around user tasks (Difficult for conversion when original authoring wasn’t focused around user-centric tasks.)

Important for future conversions:
    Remove duplicate content; write in one location and link
    Example: Cloud Feeds Concepts duplicates content

Difficulties I’m encountering:

DB2RST conversion does not handle docbook links between chapters well (e.g. sending requests to the API chapter)

RST conversion results have line breaks hard coded. Line wrapping is treated as new line start.

————



FOCUS ON USER TASKS
    Do users need to “remember to replace”? Or do they need to “replace”?
    Do users need to “use cURL to authenticate”? Or do they need to “authenticate”? 
    Structure language around the actual goal a user is trying to achieve.

Eliminate hard-coded chapter, table, and example numbering. Instead, provide implicit links to section titles. If sequential numbering is required, use automatic section numbering. http://docutils.sourceforge.net/docs/ref/rst/directives.html#automatic-section-numbering

Call out first use of an unfamiliar term. (Use italics)

Place links at end of section, organize by order of appearance.

——

Script automation for line-wrapping handling? 

Specifically call out URL formatting and conventions

Rose working on core infrastructure docs in Read the Docs default template. Can we apply template to Cloud Feeds docs?
    IAN SAYS: use Mailgun template rather than RtD template

Cloud Feeds Dev Guide
    API reference section: how to convert to RST ?
        Greg Schreck
    Get Cloud Feeds API reference to live on api.rackspace.com

Talk to Renee and Rose about Repose and conditional text (internal v external)

Focus on creating a template; concentrate on creating something to take forward for the benefit of others

Integrate hyperlinks into text rather than calling them out separately

Post-conversion cleanup

Strip out chapter, example, and table numbering.

Update links
    Preserve readability by separating the link text and the target URL.
        Put target URLs at the end of the section containing the link text.
    Explicitly label section headings for use with the :ref: tag.
        Do this even if your document is short and doesn’t reference external files. It will save work later if someone needs to reference your section or incorporate your material into a larger work.

    For example::

    # Explicitly labeling section 1 makes cross-referencing easier.
    .. _section-1:

    Section 1
    =========

    # The link text is separated from the target URL.
    Here is some `link text`_.

    Skip ahead to :ref:`section-2`.

    <everything else in the section>

    # The target URL is specified at the end of the section.
    .. _link text: https://targeturl

    # Explicit label for section 2
    .. _section-2:

    Section 2
    =========

    See :ref:`section-1`.

No need to remove line breaks in normal text.

Doc structuring: when natively authoring, structure individual files around larger groups of user tasks, not around feature sets or product names

Preserve accuracy of information between branches (legacy and empathetic fork)

Cross references: put first cross reference directive BELOW section heading, all others go ABOVE section heading

Question for #general: It’d be good to have a non-generic 404 page.

Make sure to put image path in .. image: tags, or just put image files at same hierarchy as referencing file (e.g., .. image: /images/foo.png)

Use consistent conventions for heading levels::

    =========
    Heading 1
    =========

    Heading 2
    ~~~~~~~~~

    Heading 3
    ---------
