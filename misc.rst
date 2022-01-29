
misc commands
=============

- ssh: git clone git@github.com:crapalajuive/the_one.git        # requires public SSH keys in your GitHub account
- http: git clone https://github.com/crapalajuive/the_one.git
- cli: gh repo clone crapalajuive/the_one                       # requires github cli installed


config::

   [core]
           repositoryformatversion = 0
           filemode = true
           bare = false
           logallrefupdates = true
   [remote "origin"]
           url = https://github.com/crapalajuive/the_one.git
           fetch = +refs/heads/*:refs/remotes/origin/*
   [branch "main"]
           remote = origin
           merge = refs/heads/main


create a new repository on the command line
---------------------------------------------------

.. code:: bash

   echo "# the_one" >> README.md
   git init
   git add README.md
   git commit -m "first commit"
   git branch -M main
   git remote add origin git@github.com:crapalajuive/the_one.git
   git push -u origin main

local configure settings ( optional )
---------------------------------------------------

- get token from github

.. code:: bash

   # still in repo directory, run
   git config --local user.name crapalajuive
   git config --local user.email user@domain.com
   git config --local credential.helper store
   git config --local -l

.git/config::

   ----------- snip --------
   [user]
           email = user@domain.com
           name = crapalajuive
   # this setting uses ~/.git-credentials to store github login credentials
   [credential]
           helper = store
   #       helper = cache --timeout=3600
   #       helper = cache
   ----------- snip --------


~/.git-credentials::

   ----------- snip --------
   https://user%40domain.com:<token>@github.com
   ----------- snip --------

.. note::

   | https://gituser:gitpassword@domain.xxx
   | Where domain.XXX could be github.com, bitbucket.org, or others

.. note::

   git config --global credential."https://somegithost.com".username MyUserName

push an existing repository from the command line
---------------------------------------------------

.. code:: bash

   git remote add origin git@github.com:crapalajuive/the_one.git
   git branch -M main
   git push -u origin main

GitHub Pages
------------

There're three places to populate your docs for your Github repository:

- docs/ folder
- master branch
- gh-pages branch

It is recommended that you save your files to the ./docs subfolder of the
master branch of your repository. Then select master branch /docs folder as
your Github Pages source in your repositories' settings page.

.. figure:: _static/deploy-github-pages.png
      :alt: gh-pages
      :align: center
      :scale: 50%
      :figclass: align-center
      :target: _static/deploy-github-pages.png


.. note::

   You can also save files in the root directory and select master branch. You'll need to place a **.nojekyll** file in the deploy location (such as /docs or the gh-pages branch)

refs
-----

- https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions
- https://docsify.js.org/#/deploy?id=github-pages
- https://crapalajuive.github.io/gh1/
