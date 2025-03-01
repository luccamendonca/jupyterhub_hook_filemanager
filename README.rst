JupyterHub Hook FileManager
****************************

Content Manager for Filemanager Jupyterhub with hooks support

Install
=======

::

    pip install jupyterhub_hook_filemanager


In your jupyterhub config file:

::

    from jupyterhub_hook_filemanager.hook_filemanager import HookFileContentsManager

    c.NotebookApp.contents_manager_class = HookFileContentsManager

::

    c.HookFileContentsManager.pre_get_hook = your_function
    c.HookFileContentsManager.post_get_hook = your_function

**your_function** should expect such attributes for **get** hooks:


::

    your_function(path, content, type, format, contents_manager):
        send_info(contents_manager.config, path)


::

    c.HookFileContentsManager.pre_update_hook = your_function
    c.HookFileContentsManager.post_update_hook = your_function


**your_function** should expect such attributes for **update** hooks:


::

    your_function(model, path, contents_manager):
        send_info(contents_manager.config, path, model)


::

    c.HookFileContentsManager.pre_delete_hook = your_function
    c.HookFileContentsManager.post_delete_hook = your_function

**your_function** should expect such attributes for **delete** hooks:


::

    your_function(path, contents_manager):
        send_info(contents_manager.config, path)


**pre_save_hook** and **post_save_hook** are specified at default documentation: http://jupyter-notebook.readthedocs.io/en/latest/extending/savehooks.html but should be equal to **update** hooks.


## Licensing

JupyterHub Hook FileManager is under [Apache 2 License](./LICENSE)
