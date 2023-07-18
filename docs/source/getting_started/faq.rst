.. Copyright (c) Jupyter Development Team.
.. Distributed under the terms of the Modified BSD License.

Frequently Asked Questions (FAQ)
================================

Below are some frequently asked questions. Click on a question to be directed to
relevant information in our documentation or our GitHub repo.

General
-------

-  :ref:`What is JupyterLab? <overview>`
-  :ref:`What will happen to the classic Jupyter Notebook? <classic>`
-  `Where is the official online documentation for
   JupyterLab? <https://jupyterlab.readthedocs.io>`__
-  :ref:`How can you report a bug or issue? <issue>`

Usage
-----

Notebook
^^^^^^^^

My notebook is displaying cell outputs in an `iframe <https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe>`__. They are reset when scrolling back and forth.

    Since JupyterLab v4, notebook rendering is optimized to display only the cells needed.
    This has side effects with iframes.

    The current workaround is to set the settings *Notebook* => *Windowing mode* to ``defer`` or ``none``.
    It will negatively impact the performance of JupyterLab when opening long notebooks and/or lots of files.

My notebook injects customized CSS that results in unexpected scrolling issues (e.g. it fails to scroll to the active cell).

    Since JupyterLab v4, notebook rendering is optimized to display only the cells needed.
    It does not support changing element CSS `margin <https://developer.mozilla.org/en-US/docs/Web/CSS/margin>`__
    (in particular for cells).

    The workaround is to prefer injecting customized `padding <https://developer.mozilla.org/en-US/docs/Web/CSS/padding>`__ rather than *margin*.
    If you can not avoid changing the margins, you can set the settings *Notebook* => *Windowing mode* to ``defer`` or ``none``.
    It will negatively impact the performance of JupyterLab when opening long notebooks and/or lots of files.

Tips and Tricks
---------------

- How do I start JupyterLab with a clean workspace every time?

Add ``'c.ServerApp.default_url = '/lab?reset'`` to your ``jupyter_server_config.py``.
See `How to create a jupyter_server_config.py <https://jupyter-server.readthedocs.io/en/latest/users/configuration.html>`__ for more information.

- Run Terminal Commands in Jupyter

Add '!' beforr the terminal command. For example !ls is equivalent to ls. 

- Keyboard Shortcuts
There are two different modes called Command mode and edit mode. The shortcuts below will show how to use these different shorcuts. 

Shortcuts in both modes:
   | Shift + Enter runs the current cells and selects below
   | Ctrl + Enter runs the selected cells.
   | Alt + Enter runs the current cells and inserts below. 
   | Ctrl + S saves and creates a checkpoint

While in command mode (press Esc to activate):
   | Enter to start edit mode
   | H shows all shorcuts
   | Up selects cell above
   | Down selects the cell below
   | Shift + Up extends selected cells above
   | Shift + Down extends selected cells below
   | A inserts cell above
   | B inserts cell below
   | X cut selected cells
   | C copy selected cells
   | V paste cells below
   | Shift + V paste cells below
   | Double Press D to delete selected cells
   | Z undo cell deletion
   | S save and creates checkpoint
   | Y changes the cell type to code
   | M changes the cell type to Markdown
   | P opens the command pallette
   | Shift + Space to scroll notebook up

Commands for edit mode (press Enter to activate)
   | Esc takes you into command mode
   | Tab to assist with completion or indentation
   | Shift + Table shows tooltip
   | Ctrl + ] indents
   | Ctrl + [ indents
   | Ctrl + A selects all
   | Ctrl + Z undos
   | Ctrl + Shift + Z or Ctrl + Y redo
   | Ctrl + Home goes to cell start
   | Ctrl + End goes to cell end
   | Ctrl + Left goes one word left
   | Ctrl + Right goes to one word right
   | Ctrl + Shift + P opens the command palette
   | Down moves cursor down
   | Up move cursor up


Development
-----------


-  `How can you
   contribute? <https://github.com/jupyterlab/jupyterlab/blob/main/CONTRIBUTING.md>`__
-  :ref:`How can you extend or customize JupyterLab? <user_extensions>`
-  In the classic Notebook, `I could use custom Javascript outputted by a cell to programmatically
   control the Notebook <https://stackoverflow.com/a/32769976/907060>`__. Can I do the same thing in JupyterLab?

   JupyterLab was built to support a wide variety of extensibility, including dynamic behavior based on notebook
   outputs. To access this extensibility, you should write a custom JupyterLab extension. If you would
   like trigger some behavior in response to the user executing some code in a notebook, you can output a custom
   mimetype (:ref:`rendermime`). We currently don't allow access to the JupyterLab
   API from the Javascript renderer, because this would tie the kernel and the notebook output to JupyterLab
   and make it hard for other frontends to support it.
   If you have comments or suggestions on changes here, please comment on `this issue <https://github.com/jupyterlab/jupyterlab/issues/4623>`__.
