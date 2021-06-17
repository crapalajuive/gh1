
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

push an existing repository from the command line
---------------------------------------------------

.. code:: bash

   git remote add origin git@github.com:crapalajuive/the_one.git
   git branch -M main
   git push -u origin main

