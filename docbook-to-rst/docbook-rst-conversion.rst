.. _docbook2rst:

====================================================
Converting an existing document from Docbook to reST
====================================================

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

    If your document contains nested RST markup inside of tables, the effort of manual clean-up increases significantly. It's better to remove all nested markup in Docbook before running the conversion script.

#. Remove markup in tables wherever possible.

    Sphinx handles markup in tables erratically at best. Manually repairing tables in RST is laborious and time-consuming. 

    Some examples of how markup in tables breaks through conversion:

        * Sphinx may not parse markup correctly when marked-up text breaks across table rows. 

        * Sphinx inserts a space between characters broken across table rows.

        * Sphinx may publish inline markup in tables without parsing it.

        * Sphinx does not parse cross references that break across table rows.

    Removing markup in tables prior to conversion reduces effort.

Convert your docs
~~~~~~~~~~~~~~~~~

Create a GitHub repository
--------------------------

Create a new repository for your conversion results.

Run the conversion script
-------------------------

1. Follow the instructions for `converting Docbook to RST`_.

.. _converting Docbook to RST: https://one.rackspace.com/pages/viewpage.action?title=Notes+on+converting+DocBook+to+RST&spaceKey=~marg7175

2. Move the conversion results to your new repo.

3. In your doc repo, run ``sphinx-quickstart``.

    The quickstart script guides you through setup.

4. Accept the Sphinx defaults.

    For version number, enter the current product or document version followed by 'b1`. For example::

    1.01b1

    `1.0` is the document version. 'b1' indicates that this is the first version of a document converted from an existing document. (If the document or product version remains unchanged, the next iteration's version number would be 1.0b2.)

Clean up your reST
~~~~~~~~~~~~~~~~~~

Set up your authoring environment
---------------------------------

Choose a code editor that supports RST markup.

..note:: `Sublime Text`_ offers native RST support.

Follow OpenStack conventions for `authoring in RST`_. Specifically:

    * Use consistent heading formats.::

        =========
        Heading 1
        =========

        Heading 2
        ~~~~~~~~~

        Heading 3
        ---------

    * Enable word wrapping at 70 columns.

    * Use \`\` for inline code. For example::

        This looks like ``inline code markup``.

(Note to self: make a wiki page that simplifies OpenStack conventions for RST.)

.. _authoring in RST: https://wiki.openstack.org/wiki/Documentation/Markup_conventions
.. _Sublime Text: http://www.sublimetext.com/2

Rename your files
-----------------

#. Choose meaningful names for individual doc files. For example, `api-reference` is better than `chapter2`.

Edit your index.rst file
------------------------

1. Open the `index.rst` file in the top level of your doc repo.

2. Create the navigation structure for your document.

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

Clean up tables
---------------

Tables require significant manual cleanup post-conversion. 

#. Remove markup in tables whenever possible. 

#. Remove markup from text in bulleted or itemized lists. 

    RST treats markup as an unexpected termination of the list.

#. Remove cross references from tables.

    If a cross reference is necessary, replace all cross references inside a table with a single cross reference after the table.

Clean up line breaks
--------------------

#. Remove breaks between lines in the same paragraph.

The conversion script inserts a break at the end of every line, which may cause markup to parse incorrectly.

Repair links and cross-references
---------------------------------

#. Repair external links.

    With hyperlinks, RST allows you to separate link text from the link anchor. This helps preserve readability and makes it easier to update link URLs.

    When linking to an external URL, place link anchors at the bottom of the section. For example::

        =========
        Heading 1
        =========

        `foo`_.

        <other text>

        .. _foo: http://bar.com

        Heading 2
        ~~~~~~~~~

#. Assign cross reference IDs.

    Add cross reference IDs to each section heading in your book. Follow the format::

        <standard_abbreviation-book_abbreviation-heading1-heading2-heading3>

    For example, the abbreviation for the top-level heading in the overview for the Cloud Load Balancer Developer Guide would be::

        clb-devguide-overview

    * Follow the standard list of `unique Disqus identifiers`_ for product abbreviations.

    * Place cross reference IDs before the ID's section heading, and include a blank line after each cross reference directive. For example::

        .. _clb-devguide-overview:

        =========
        Heading 1
        =========

#. Create cross references with the ``:ref:`` directive::

    This is a :ref:`cross reference <cross-reference-target>`.

.. _unique Disqus identifiers: https://one.rackspace.com/pages/viewpage.action?title=Disqus+project+identifiers&spaceKey=devdoc

Repair image links
------------------

#. Link images in RST with the ``image`` directive. For example::

    .. image: /images/foo.png

.. note::
    Be sure to include the image's relative path.

Remove table, example, and chapter numbering
--------------------------------------------

#. Remove chapter, table, and example numbers.

#. Replace explicit links to tables and examples with cross references to the section containing the table or example.

(Note to reviewers: Does it make sense to remove numbering in Docbook prior to conversion? Removing numbering in RST output is pretty painless, so it may make more sense to remove numbering post-conversion.)

Test your output
----------------

#. `Follow these steps`_ to build HTML files from your RST source.

Repeat the ``make`` process to test your updates.

.. _Follow these steps: https://one.rackspace.com/display/devdoc/Sphinx+documentation+notes+for+multi-product+user+guides

Commit your output
------------------

Add the ``_build`` directory to your GitHub repo.

.. note::
    Commit changes regularly&mdash;at least once per day.
