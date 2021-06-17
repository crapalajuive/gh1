
=============================
demo 1 - basic page
=============================

.. topic:: Abstract
   :class: output

       | how to setup github pages for a repository
       | line 2

.. figure:: _static/github-icon.svg
      :alt: gh-pages
      :align: center
      :scale: 50%
      :figclass: align-center
      :target: _static/github-icon.svg

pre
-----------

- github account
- git / github knowledge
- git installed locally


repo
------

@github

- create new repo "new_repo"
   - priv/pub (either)
   - add Readme file ( so not empty repo )

@local (terminal)

- mkdir my_repos ; cd my_repos
- git clone https://github/<user>/new_repo.git
- cd new_repo
- create index.html
- git status # main branch
- git add .
- git commit -m "initial commit"
- git push origin main

@github

- settings -> github pages -> source = main (root)
- site generated: https://<user>.github.io/new_repo


make changes
------------

@local

.. code:: bash

   git checkout -b styling
   create styles.css
   git status # styling branch
   git add .
   git commit -m "initial css"
   git push origin styling

@github

- pull request to merge into the main branch


alternative branch for docs
----------------------------

@local

.. code:: bash

   git checkout -b docs
   git push origin docs

@github

- settings -> github pages -> source = docs (root)
- site generated is still: https://<user>.github.io/new_repo
