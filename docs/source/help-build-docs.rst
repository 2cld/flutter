Help with Building the Docs
===========================

=================
Build ReadTheDocs
=================

To edit and update the readthedocs::

 $ cd ~/2cld
 $ git clone https://github.com/2cld/flutter
 $ cd flutter/docs
 $ make html
 $ open build/html/index.html
 $ vi source/help.rst
 $ make html
 $ open build/html/index.html
 (verify changes)
 $ make clean
 $ cd ~/2cld/flutter
 $ git add *
 $ git commit -m "Update documents"
 $ git push
 (wait some min for webhooks to hit)
 $ open http://2cldflutter.readthedocs.io/en/latest/
 (inspect changes)

==============
Sphinx Install
==============

To install Sphinx via pip ( pip-install_ ) to make documentation::

 $ python --version
 Python 2.7.10
 $ python get-pip.py
 $ pip --version
 pip 9.0.1 from /Library/Python/2.7/site-packages (python 2.7)
 $ sudo pip install --ignore-installed Sphinx

=================
Add key to github
=================

Add your ssh key to github via github-addkey_ ::

 macci:~ cat$ pbcopy < ~/.ssh/id_rsa.pub

Login to github.  Click your picture, select settings.  Select SSH and GPG keys.  Paste key to add.

===============
git repo config
===============

The .git/config file should look like this::

    [core]
            repositoryformatversion = 0
            filemode = true
            bare = false
            logallrefupdates = true
            ignorecase = true
            precomposeunicode = true
    [remote "origin"]
            url = https://gituser:gitpass@github.com/2cld/flutter.git
            fetch = +refs/heads/*:refs/remotes/origin/*
    [branch "master"]
            remote = origin
            merge = refs/heads/master


==========
ssh keygen
==========

Generate a new key via github-genkey_ process for macmini::

 macci:~ cat$ ssh-keygen -t rsa -b 4096 -C "whoever@whatever.com"

Modify ~/.ssh/config to contain::

    Host *
     AddKeysToAgent yes
     UseKeychain yes
     IdentityFile ~/.ssh/id_rsa

Now add the key to ssh-agent keychain::

 macci:~ cat$ eval "$(ssh-agent -s)"
 macci:~ cat$ ssh-add -K ~/.ssh/id_rsa

=================
xcode git install
=================

Assuming Mac OSX 10.13.3 fresh install on macmini named macci.  To install git and xcode on macci::

 macci:~ cat$ git --version

This will activate the xcode install pop-up and configure machine with xcode cli.

Set your git global info::

 macci:flutter cat$ git config --global --edit

==========
References
==========

 + Docs created via Sphinx_
 + rst-cheatsheet_ 
 + pip-install_
 + yarn_ is a new npm (node package manager)

.. _Sphinx: http://www.sphinx-doc.org/en/stable/tutorial.html
.. _rst-cheatsheet: https://github.com/ralsina/rst-cheatsheet/blob/master/rst-cheatsheet.rst
.. _pip-install: https://pip.pypa.io/en/stable/installing/
.. _yarn: https://yarnpkg.com/en/docs/cli
.. _github-genkey: https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/
.. _github-addkey: https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/
