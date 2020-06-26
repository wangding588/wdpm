===============
How to Develope
===============

.. image:: https://travis-ci.org/wangding588/wdpm.png?branch=master
    :target: https://travis-ci.org/wangding588/wdpm

.. See how to add travis ci image from https://raw.githubusercontent.com/demizer/go-rst/master/README.rst
   https://github.com/demizer/go-rst/commit/9651ab7b5acc997ea2751845af9f2d6efee825df

Development Tool: Pelican_ (static site generator written in Python)

Development Environment: `Ubuntu 20.04`_

Theme from `Bootstrap 4.5 Carousel Example`_


First-time Setup
----------------

1. Install git_ and pip_:

   .. code-block:: bash

     $ sudo apt-get install git
     $ sudo apt-get install python3-pip

2. Install language packages to add locale (English, Traditional Chinese in this
   example):

   .. code-block:: bash

     $ sudo apt-get install language-pack-en
     $ sudo apt-get install language-pack-zh-hant

3. git clone source code:

   .. code-block:: bash

     $ cd
     $ mkdir dev
     $ cd ~/dev/
     $ git clone https://github.com/wangding588/wdpm.git wdpm

4. Install Python tools:

   .. code-block:: bash

     $ cd ~/dev/wdpm/
     $ sudo pip install -r requirements.txt

5. Install Pelican `i18n_subsites`_ plugin:

   .. code-block:: bash

     $ cd ~/dev/wdpm/
     $ make download

6. Generate CSS file:

   .. code-block:: bash

     $ cd ~/dev/wdpm/
     $ make scss


Auto-deploy by `Travis CI`_
---------------------------

See `GitHub Pages Deployment - Travis CI`_.

First save your `personal access token`_ in `repository settings`_.

For User Pages, the following is sample config:

.. code-block:: yaml

  deploy:
    provider: pages
    repo: USERNAME/USERNAME.github.io
    target_branch: master
    skip_cleanup: true
    github_token: $GITHUB_TOKEN
    local_dir: output
    on:
      branch: master

For Project Pages, the following is sample config:

.. code-block:: yaml

  deploy:
    provider: pages
    skip_cleanup: true
    github_token: $GITHUB_TOKEN
    local_dir: output
    on:
      branch: master


Daily Development
-----------------

.. code-block:: bash

    # start edit and develope
    $ cd ~/dev/wdpm/
    # If something changes, re-generate the website:
    $ make html
    # start dev server
    $ make
    # open your browser and preview the website at http://localhost:8000/


Note for `Google Adsense`_
++++++++++++++++++++++++++

Edit the following three files to include your code:

- `theme/templates/layout/includes/adsense.html <theme/templates/layout/includes/adsense.html>`_
- `theme/templates/layout/includes/adsense_page_level.html <theme/templates/layout/includes/adsense_page_level.html>`_
- `plugins/adsense/adsense.py <plugins/adsense/adsense.py>`_

Add ``:adsense: yes`` to the articles that you want to put ads in. See
`content/articles/2016/02/16/c-hello-world%en.rst <content/articles/2016/02/16/c-hello-world%en.rst>`_
for example.
Or use directive to include ads in articles. See raw file of
`content/articles/2016/02/16/c-hello-world%zh.rst <content/articles/2016/02/16/c-hello-world%zh.rst>`_
for example.


References
----------

.. [1] `Deploy Website by Pelican, Travis CI, and GitHub Pages <https://siongui.github.io/2016/01/05/deploy-website-by-pelican-travis-ci-github-pages/>`_

.. [2] JINJA_FILTERS in `Settings — Pelican documentation <http://docs.getpelican.com/en/latest/settings.html>`_

       `Jinja custom filters documentation <http://jinja.pocoo.org/docs/dev/api/#custom-filters>`_

.. [3] `王鼎貴金屬 <http://www.wdpm.com.tw/>`_

.. [4] | `embed gold price chart - Google search <https://www.google.com/search?q=embed+gold+price+chart>`_
       | `embed gold price chart - DuckDuckGo search <https://duckduckgo.com/?q=embed+gold+price+chart>`_
       | `embed gold price chart - Ecosia search <https://www.ecosia.org/search?q=embed+gold+price+chart>`_
       | `embed gold price chart - Qwant search <https://www.qwant.com/?q=embed+gold+price+chart>`_
       | `embed gold price chart - Bing search <https://www.bing.com/search?q=embed+gold+price+chart>`_
       | `embed gold price chart - Yahoo search <https://search.yahoo.com/search?p=embed+gold+price+chart>`_
       | `embed gold price chart - Baidu search <https://www.baidu.com/s?wd=embed+gold+price+chart>`_
       | `embed gold price chart - Yandex search <https://www.yandex.com/search/?text=embed+gold+price+chart>`_

.. [5] | `Gold Price <https://goldprice.org/>`_
       | `KITCO <https://www.kitco.com/>`_
       | `Embed a gold price chart on your website | BullionVault <https://www.bullionvault.com/help/custom_gold_price_charts.html>`_
       | `Gold Price Charts <https://goldprice.org/gold-price-charts.html>`_
       | `Latest gold, silver, platinum, palladium and rhodium prices. <https://www.kitco.com/price/>`_
       | `Free Stock Widgets — Financial Web Components — TradingView <https://www.tradingview.com/widget/>`_
       | `免費股票小工具 - 金融Web組件 — TradingView <https://tw.tradingview.com/widget/>`_
       |

.. _Pelican: http://blog.getpelican.com/
.. _Ubuntu 20.04: http://releases.ubuntu.com/20.04/
.. _UNLICENSE: http://unlicense.org/
.. _git: https://git-scm.com/
.. _pip: https://pypi.python.org/pypi/pip
.. _i18n_subsites: https://github.com/getpelican/pelican-plugins/tree/master/i18n_subsites
.. _Travis CI: https://travis-ci.org/
.. _GitHub Pages Deployment - Travis CI: https://docs.travis-ci.com/user/deployment/pages/
.. _personal access token: https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/
.. _repository settings: https://docs.travis-ci.com/user/environment-variables#Defining-Variables-in-Repository-Settings
.. _Google Adsense: https://www.google.com/search?q=Google+AdSense
.. _Bootstrap 4.5 Carousel Example: https://getbootstrap.com/docs/4.5/examples/carousel/
