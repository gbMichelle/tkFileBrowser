This version of tkfilebrowser does not make paths absolute, this is a requirement for another project I am working on. Once that project has a better solution for this this fork won't update anymore. Feel free to use it, but beware.

tkfilebrowser
=============

|Release| |Linux| |Windows| |Travis| |Codecov| |License| |Doc|

tkfilebrowser is an alternative to tkinter.filedialog that allows the
user to select files or directories. The GUI is written with tkinter but
the look is closer to GTK and the application uses GTK bookmarks (the
one displayed in nautilus or thunar for instance). This filebrowser
supports new directory creation and filtype filtering.

This module contains a general ``FileBrowser`` class which implements the
filebrowser and the following functions, similar to the one in filedialog:

    * ``askopenfilename`` that allow the selection of a single file

    * ``askopenfilenames`` that allow the selection of multiple files

    * ``askopendirname`` that allow the selection a single folder

    * ``askopendirnames`` that allow the selection of multiple folders

    * ``asksaveasfilename`` that returns a single filename and give a warning if the file already exists


The documentation is also available here: https://tkfilebrowser.readthedocs.io

.. contents:: Table of Contents


Requirements
------------

- Linux or Windows
- Python 2.7 or 3.x

And the python packages:

- tkinter (included in the python distribution for Windows)
- `psutil <https://pypi.org/project/psutil/>`_
- `babel <https://pypi.org/project/babel/>`_
- `pywin32 <https://pypi.org/project/pywin32/>`_ (Windows only)
- `pillow <https://pypi.org/project/pillow/>`_ (only if tkinter.TkVersion < 8.6)


Installation
------------

- Ubuntu: use the PPA `ppa:j-4321-i/ppa <https://launchpad.net/~j-4321-i/+archive/ubuntu/ppa>`__

    ::

        $ sudo add-apt-repository ppa:j-4321-i/ppa
        $ sudo apt-get update
        $ sudo apt-get install python(3)-tkfilebrowser


- Archlinux:

    the package is available on `AUR <https://aur.archlinux.org/packages/python-tkfilebrowser>`__


- With pip:

    ::

        $ pip install tkfilebrowser


Documentation
-------------

* Optional keywords arguments common to each function

    - parent: parent window

    - title: the title of the filebrowser window

    - initialdir: directory whose content is initially displayed

    - initialfile: initially selected item (just the name, not the full path)

    - filetypes list: [("name", "\*.ext1|\*.ext2|.."), ...]
      only the files of given filetype will be displayed,
      e.g. to allow the user to switch between displaying only PNG or JPG
      pictures or dispalying all files:
      filtypes=[("Pictures", "\*.png|\*.PNG|\*.jpg|\*.JPG'), ("All files", "\*")]

    - okbuttontext: text displayed on the validate button, if None, the
      default text corresponding to the mode is used (either "Open" or "Save")

    - cancelbuttontext: text displayed on the button that cancels the
      selection.

    - foldercreation: enable the user to create new folders if True (default)

* askopendirname

    Allow the user to choose a single directory. The path of the
    chosen directory is returned. If the user cancels, an empty string is
    returned.

* askopendirnames

    Allow the user to choose multiple directories. A tuple containing the
    path of the chosen directories is returned. If the user cancels,
    an empty tuple is returned.

* askopenfilename

    Allow the user to choose a single file. The path of the
    chosen file is returned. If the user cancels, an empty string is
    returned.

* askopenfilenames

    Allow the user to choose multiple files. A tuple containing the
    path of the chosen files is returned. If the user cancels,
    an empty tuple is returned.

* asksaveasfilename

    Allow the user to choose a file path. The file may not exist but
    the path to its directory does. If the file already exists, the user
    is asked to confirm its replacement.

    Additional option:

        - defaultext: extension added to filename if none is given (default is none)


Changelog
---------

- Changes below made by gbMichelle:

- tkfilebrowser 2.4.0
    * Make returned paths not absolute.
    * Added aliases askdirectory & askdirectories for functions askopendirname & askopendirnames.
    * Made it so that only / and user mounts get displayed on linux.
    * Set minimum window size to 600x400 instead of it having no minimum.

- Changes below were made by the original author Juliette Monsel:

- tkfilebrowser 2.3.2
    * Show networked drives on Windows
    * Fix click on root button in path bar

- tkfilebrowser 2.3.1
    * Fix path bar navigation in Linux

- tkfilebrowser 2.3.0
    * Make package compatible with Windows
    * Set initial focus on entry in save mode

- tkfilebrowser 2.2.6
    * No longer reset path bar when clicking on a path button
    * Fix bug caused by broken links

- tkfilebrowser 2.2.5
    * Add compatibility with Tk < 8.6.0 (requires PIL.ImageTk)
    * Add desktop icon in shortcuts
    * Fix handling of spaces in bookmarks
    * Fix bug due to spaces in recent file names

- tkfilebrowser 2.2.4
    * Fix bug in desktop folder identification

- tkfilebrowser 2.2.3
    * Fix FileNotFoundError if initialdir does not exist
    * Add Desktop in shortcuts (if found)
    * Improve filetype filtering

- tkfilebrowser 2.2.2
    * Fix ValueError in after_cancel with Python 3.6.5

- tkfilebrowser 2.2.1
    * Fix __main__.py for python 2

- tkfilebrowser 2.2.0
    * Use babel instead of locale in order not to change the locale globally
    * Speed up (a little) folder content display
    * Improve example: add comparison with default dialogs
    * Add select all on Ctrl+A if multiple selection is enabled
    * Disable folder creation button if the user does not have write access
    * Improve extension management in save mode

- tkfilebrowser 2.1.1
    * Fix error if LOCAL_PATH does not exists or is not writtable

- tkfilebrowser 2.1.0
    * Add compatibility with tkinter.filedialog keywords 'master' and 'defaultextension'
    * Change look of filetype selector
    * Fix bugs when navigating without displaying hidden files
    * Fix color alternance bug when hiding hidden files
    * Fix setup.py
    * Hide suggestion drop-down when nothing matches anymore

- tkfilebrowser 2.0.0
    * Change package name to tkfilebrowser to respect PEP 8
    * Display error message when an issue occurs during folder creation
    * Cycle only through folders with key browsing in "opendir" mode
    * Complete only with folder names in "opendir" mode
    * Fix bug: grey/white color alternance not always respected
    * Add __main__.py with an example
    * Add "Recent files" shortcut
    * Make the text of the validate and cancel buttons customizable
    * Add possibility to disable new folder creation
    * Add python 2 support
    * Add horizontal scrollbar

- tkFileBrowser 1.1.2
    * Add tooltips to display the full path of the shortcut if the mouse stays
      long enough over it.
    * Fix bug: style of browser treeview applied to parent

- tkFileBrowser 1.1.1
    * Fix bug: key browsing did not work with capital letters
    * Add specific icons for symlinks
    * Add handling of symlinks, the real path is returned instead of the link path

- tkFileBrowser 1.1.0
    * Fix bug concerning the initialfile argument
    * Add column sorting (by name, size, modification date)

- tkFileBrowser 1.0.1
    * Set default filebrowser parent to None as for the usual filedialogs and messageboxes.

- tkFileBrowser 1.0.0
    * Initial version


Example
=======

.. code:: python

    try:
        import tkinter as tk
        import tkinter.ttk as ttk
        from tkinter import filedialog
    except ImportError:
        import Tkinter as tk
        import ttk
        import tkFileDialog as filedialog
    from tkfilebrowser import askopendirname, askopenfilenames, asksaveasfilename


    root = tk.Tk()

    style = ttk.Style(root)
    style.theme_use("clam")


    def c_open_file_old():
        rep = filedialog.askopenfilenames(parent=root, initialdir='/', initialfile='tmp',
                                          filetypes=[("PNG", "*.png"), ("JPEG", "*.jpg"), ("All files", "*")])
        print(rep)


    def c_open_dir_old():
        rep = filedialog.askdirectory(parent=root, initialdir='/tmp')
        print(rep)


    def c_save_old():
        rep = filedialog.asksaveasfilename(parent=root, defaultextension=".png", initialdir='/tmp', initialfile='image.png',
                                           filetypes=[("PNG", "*.png"), ("JPEG", "*.jpg"), ("All files", "*")])
        print(rep)


    def c_open_file():
        rep = askopenfilenames(parent=root, initialdir='/', initialfile='tmp',
                               filetypes=[("Pictures", "*.png|*.jpg|*.JPG"), ("All files", "*")])
        print(rep)


    def c_open_dir():
        rep = askopendirname(parent=root, initialdir='/', initialfile='tmp')
        print(rep)


    def c_save():
        rep = asksaveasfilename(parent=root, defaultext=".png", initialdir='/tmp', initialfile='image.png',
                                filetypes=[("Pictures", "*.png|*.jpg|*.JPG"), ("All files", "*")])
        print(rep)


    ttk.Label(root, text='Default dialogs').grid(row=0, column=0, padx=4, pady=4, sticky='ew')
    ttk.Label(root, text='tkfilebrowser dialogs').grid(row=0, column=1, padx=4, pady=4, sticky='ew')
    ttk.Button(root, text="Open files", command=c_open_file_old).grid(row=1, column=0, padx=4, pady=4, sticky='ew')
    ttk.Button(root, text="Open folder", command=c_open_dir_old).grid(row=2, column=0, padx=4, pady=4, sticky='ew')
    ttk.Button(root, text="Save file", command=c_save_old).grid(row=3, column=0, padx=4, pady=4, sticky='ew')
    ttk.Button(root, text="Open files", command=c_open_file).grid(row=1, column=1, padx=4, pady=4, sticky='ew')
    ttk.Button(root, text="Open folder", command=c_open_dir).grid(row=2, column=1, padx=4, pady=4, sticky='ew')
    ttk.Button(root, text="Save file", command=c_save).grid(row=3, column=1, padx=4, pady=4, sticky='ew')

    root.mainloop()

.. |Release| image:: https://badge.fury.io/py/tkfilebrowser.svg
    :alt: Latest Release
    :target: https://pypi.org/project/tkfilebrowser/
.. |Linux| image:: https://img.shields.io/badge/platform-Linux-blue.svg
    :alt: Platform Linux
.. |Windows| image:: https://img.shields.io/badge/platform-Windows-blue.svg
    :alt: Platform Windows
.. |Travis| image:: https://travis-ci.org/j4321/tkFileBrowser.svg?branch=master
    :target: https://travis-ci.org/j4321/tkFileBrowser
    :alt: Travis CI Build Status
.. |Codecov| image:: https://codecov.io/gh/j4321/tkFileBrowser/branch/master/graph/badge.svg
    :target: https://codecov.io/gh/j4321/tkFileBrowser
    :alt: Code coverage
.. |License| image:: https://img.shields.io/github/license/j4321/tkFileBrowser.svg
    :target: https://www.gnu.org/licenses/gpl-3.0.en.html
    :alt: License
.. |Doc| image:: https://readthedocs.org/projects/tkfilebrowser/badge/?version=latest
    :target: https://tkfilebrowser.readthedocs.io/en/latest/?badge=latest
    :alt: Documentation Status
