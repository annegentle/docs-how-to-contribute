==============================
Author guide to converted docs
==============================

The first phase of Project Nexus is almost complete! 

DevDocs authors, this guide helps you resume ownership of your Docbook-to-RST converted developer guides.

Getting started
~~~~~~~~~~~~~~~

If you're new to RST/Sphinx (or if it's been a while), check out the following resources.

RST
---

Make sure you follow the `Rackspace guide to RST`_.

`Quick ReStructuredText`_ provides a reference to common RST syntax. The follow sections may be especially helpful:

    - `Inline markup`_

    - `Indentation`_

    - `How to link`_

These table creation tools can help:

    - `Plain text tables`_

    - `Format text as a table`_

.. _Rackspace guide to RST: https://one.rackspace.com/pages/viewpage.action?title=RST&spaceKey=devdoc
.. _Quick ReStructuredText: http://docutils.sourceforge.net/docs/user/rst/quickref.html

.. _Inline markup: http://docutils.sourceforge.net/docs/user/rst/quickref.html#inline-markup
.. _Indentation: http://docutils.sourceforge.net/docs/user/rst/quickref.html#block-quotes
.. _How to link: http://docutils.sourceforge.net/docs/user/rst/quickref.html#hyperlink-targets

.. _Plain text tables: http://www.tablesgenerator.com/text_tables
.. _Format text as a table: http://www.sensefulsolutions.com/2010/10/format-text-as-table.html

Sphinx
------

Visit the official site for `Sphinx`_.

.. _Sphinx: http://sphinx-doc.org/ 

Next Steps
~~~~~~~~~~

- Locate your converted RST files.

- Set up your local environment for authoring in RST/Sphinx.

- Prepare your devguides for publication.

- If you need help, there's a list of known issues at the bottom of the page.

Questions? Issues? Reach out to the `devdoc migration channel`_.

.. _devdoc migration channel: https://rackdx.slack.com/messages/devdoc-migration/

Locate your converted files
---------------------------

#. Find the RST conversion results for each of your developer guides.

Converted RST files reside in a separate ``rst/`` folder in your devguide repo. For example:

        ``https://github.com/rackerlabs/docs-cloud-files/rst/``

Set up your environment
-----------------------

Install the tools you need:

#. Install `virtualenv <https://pypi.python.org/pypi/virtualenv>`_.

    Run the following command as a superuser in your shell terminal::

        pip install --upgrade virtualenv

    If the installation fails, try installing as a superuser:

        ``sudo pip install --upgrade virtualenv``

    Enter your password when prompted.

#. Install Sphinx.

    Run the following command as a superuser in your shell terminal:

        ``pip install --upgrade sphinx``

Create new Sphinx projects
--------------------------

Repeat these steps for each of your developer guides.

#. Open your shell terminal.

#. Navigate to the developer guide's RST source directory. For example: ``/cloud-files/dev-guide/``

#. Temporarily rename your ``index.rst`` file.

    The Sphinx quickstart script will not overwrite an existing ``index.rst`` file. Renaming it temporarily allows ``sphinx-quickstart`` to complete:

        ``mv index.rst index2.rst``

    Be sure to restore your original ``index.rst`` file after the quickstart script completes.

#. Create a new Sphinx project.

    Enter the following command:

        ``sphinx-quickstart``

    The script prompts you for project parameters.

    #. Accept all defaults except: 

        - Enter the name of the repository for the project name.

            For example: ``docs-cloud-files``

        - When prompted for your name, enter your Rackspace SSO.

            For example: ``foobar1234``

        - Enter the product API version for the project version and project release version.

            For example, enter ``2.0`` as the project version and project release version for the Cloud Files API v2.0.

#. Restore your original ``index.rst`` file.

    Enter the following command:

        ``mv index2.rst index.rst``

Build HTML files from the RST source
------------------------------------

Repeat these steps for each of your developer guides.

#. Open your shell terminal.

#. Navigate to the developer guide's RST source directory. For example: ``/cloud-files/dev-guide/``

    Verify that your devguide's RST source directory contains the following files:

        ```
        conf.py
        index.rst
        ```

#. Build HTML files from your devguide's RST source with the following command:

    ``make html``

#. Verify that the build script succeeded.

    #. Navigate in your RST source folder to ``_build/html/``.

    #. Open ``index.html`` in your browser.

Prepare your devguides for publication
--------------------------------------

#. Update your docs.

    Make sure your RST files reflect any updates made after conversion began.

#. Update or remove broken links.

#. Update the HTML output.

    Run ``make html`` to update your devguide's HTML output.

Issues
~~~~~~

Inline literals display incorrectly
-----------------------------------

Verify that double back quotes `` \`\` `` enclose the literal characters.
