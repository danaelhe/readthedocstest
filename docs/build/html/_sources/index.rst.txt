.. digitalocean documentation master file, created by
   sphinx-quickstart on Fri Sep 30 15:26:48 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

#########################################
:mod:`digitalocean` --- DigitalOcean Python library
#########################################

.. module:: digitalocean

:mod:`digitalocean` is a Python client library for DigitalOceans's `HTTP API
<https://docs.digitalocean.com/reference/api/api-reference/>`_.

Installation
============

Install from PyPI::

    pip install digitalocean


Initialization
==============

:mod:`digitalocean` must be initialized with :meth:`digitalocean.client`. A
DigitalOcean API Token is required. The token can be passed explicitly to :meth:`datadog.client` or defined as environment variables
``DIGITALOCEAN_TOKEN``.

Here's an example of initializing the DigitalOcean Python Client::

   from digitalocean import Client

   client = Client(token="<DIGITALOCEAN_TOKEN>")  

.. autofunction:: digitalocean.Client

Example
===========
You can find an example of using the DigitalOcean Python client `here
<https://github.com/digitalocean/digitalocean-client-python/blob/main/examples/poc_droplets_volumes_sshkeys.py>`_.
The example walks through the process of creating a droplet with a specified ssh key, creating a volume, and then attaching the volume to the droplet. 

Pagination
~~~~~~~~~~~
Below is an example on handling pagination. One must parse the URL to find the next page::

   resp = self.client.ssh_keys.list(per_page=50, page=page)
   pages = resp.links.pages
      if 'next' in pages.keys():
            parsed_url = urlparse(pages['next'])
            page = parse_qs(parsed_url.query)['page'][0]
      else:
            paginated = False


digitalocean.Client Usage
===========

.. automodule:: digitalocean.operations
   :members:
   :undoc-members:
   :show-inheritance: