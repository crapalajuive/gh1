
misc commands
=============

- ssh: git clone git@github.com:crapalajuive/gh1.git            # requires public SSH keys in your GitHub account
- http: git clone https://github.com/crapalajuive/gh1.git
- cli: gh repo clone crapalajuive/gh1                           # requires github cli installed


config::

   [core]
           repositoryformatversion = 0
           filemode = true
           bare = false
           logallrefupdates = true
   [remote "origin"]
           url = https://github.com/crapalajuive/gh1.git
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
   git remote add origin git@github.com:crapalajuive/gh1.git
   git push -u origin main

git local configuration ( optional )
---------------------------------------------------

Generate new github token

.. figure:: _static/github_token.png
      :alt: Generate new github token
      :align: center
      :scale: 50%
      :figclass: align-center
      :target: _static/github_token.png

- https://github.com/settings/tokens

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


example ~/.git-credentials::

   ----------- snip --------
   https://user%40domain.com:<token>@github.com
   ----------- snip --------

.. note::

   | https://gituser:gitpassword@domain.xxx
   | Where domain.XXX could be github.com, bitbucket.org, or others

.. note::

   git config --global credential."https://somegithost.com".username MyUserName

ssh key configuration ( optional )
---------------------------------------------------

Generate ssh key (for github site or deploy key per repository)

.. code:: bash

   cd ~/.ssh/
   ssh-keygen -v -t rsa -b 4096 -f ${PWD}/id_rsa.github -C "crapalajuive@github" -N ""
   # or
   ssh-keygen -v -t ed25519 -a 100 -f ${PWD}/id_ed25519.github -C "crapalajuive@github" -N ""

Copy the contents of the file ~/.ssh/id_rsa.github.pub to your SSH keys in your GitHub account settings https://github.com/settings/keys

~/.ssh/config::

   ------------- snip ---------------
   Host github.com
     IdentityFile ~/.ssh/id_rsa.github
   ------------- snip ---------------

test connection

.. code:: bash

   ssh -T git@github.com

clone repo

.. code:: bash

   git clone ssh://git@github.com/crapalajuive/gh1.git
   git config --local user.name crapalajuive
   git config --local user.email user@domain.com
   git config --local -l

.. note::

   git remote set-url origin git@github.com:username/your-repository.git


push an existing repository from the command line
---------------------------------------------------

.. code:: bash

   git remote add origin git@github.com:crapalajuive/gh1.git
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
- https://github.com/settings/tokens
- https://github.com/settings/keys
- hugo?
- https://github.com/crapalajuive/gh1/settings/pages
