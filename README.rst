=================
NS8 documentation
=================

Sphinx documentation sources for NS8 documentations.

Under the root directory there are some specials files:

* conf.py: Sphinx configuration
* Makefile: Sphinx build makefile
* index.rst: document structure

All other ``.rst`` files are chapters of the manual.  If you wish to add a new
chapter, create a new file and add it to the index.rst file.

How to contribute
=================

The easiest way to contribute is by forking and editing the repository 
directly on GitHub:

* Create a GitHub account if you don't already have it
* Go to https://github.com/NethServer/ns8-docs and fork the project
* You can now edit any page using GitHub web interface and see a live preview of the output
* When you're done, simply create a new pull request
* A new automatic build is launched after the pull request is merged by a developer

While editing, please follow the guidelines below.

Editing guidelines
------------------

The document must start with a title such as ::

    ==============
    Document title
    ==============

Make sure to add only *one* first-level title for each rst file.

Next headers levels are::

    First level
    ===========

    Second level
    ------------

    Third level
    ^^^^^^^^^^^

    Fourth level
    ~~~~~~~~~~~~


To create cross-references set a label before headers, with ``-section`` suffix::

    .. _mytitle-section:

    My title
    --------

In other documents refer to "My title" with the ``:ref:`` command::
    
    More informations are explained on :ref:`mytitle-section`
    

Use the \* character for unordered list ::
 
    * First element
    * Second element

Use a definition list when describing fields ::

    My field
        This is my description

A field description can also contain a bullet list ::

    My field
        This is my description

        * First element
        * Second element

Highlight important words ::
   
    This is and *important* word.
    
Add notes with ::
    
    .. note:: Highlight this text

Add warnings with ::

    .. warning:: Warning text fragments


    
You can find more info about **RST Inline Markup** here: rst-cheatsheet_

.. _rst-cheatsheet: https://github.com/ralsina/rst-cheatsheet/blob/master/rst-cheatsheet.rst
 

Do not use *NethServer* name inside documentation. Any time you need to add the product name, 
use the *product* macro::

  |product| has this amazing feature!

Output will be::

  NethServer has this amazing feature!

The same applies to *download_site* macro.

Use semantic markup whenever possible. Recommended RST roles are:

* guilabel
* file
* command
* menuselection

Remember to emphasize system object with *:dfn:*, only the first time you mention them inside a section.
For example if you are naming a system user::

 The :dfn:`admin` user is mighty powerful.

Also take care of indexing important content. You must index a word only one time per section::
 
 The :dfn:`admin` user is mighty powerful.
 Remember to change the :index:`admin` password.

The output will be a paragraph where the first *admin* word will be italic, the latter will use standard font
but it will be indexed.

See also: http://sphinx-doc.org/markup/inline.html

Use a spell checker program before submitting a pull request. For instance run ::

  hunspell -d en_US <filename>

Build documentation
===================

Whenever there are modifications, a build process will be launched from Read the Docs site.

If you wish to build documentation locally on your machine, make sure to install all Sphinx packages.

On Fedora 24 or later use: ::

  sudo dnf install python2-sphinx python2-sphinx-bootstrap-theme

Then, install all required modules: ::

  sudo pip install -r requirements.txt

First clone the repository, enter the inside the cloned directoru and type ::

   make html

Localization workflow
---------------------

Generate po files for a new language: ::

   make gettext
   sphinx-intl update -p _build/gettext -l it

Documentation style guidelines
==============================

Please follow 

https://www.writethedocs.org/blog/newsletter-december-2016/#simplifying-and-tightening-your-writing
https://www.writethedocs.org/blog/newsletter-october-2022/#gerunds-in-headings
https://www.writethedocs.org/blog/newsletter-september-2022/#when-to-use-acronyms
https://www.writethedocs.org/blog/newsletter-november-2019/#you-sing-the-second-person-in-documentation
https://www.writethedocs.org/blog/newsletter-may-2018/#using-imperatives-in-documentation
https://www.writethedocs.org/blog/newsletter-july-2017/#documenting-unlabeled-buttons
https://learn.microsoft.com/en-us/style-guide/global-communications/writing-tips
