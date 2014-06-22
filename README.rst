Namesync
========

Sync DNS records stored in a flat file format to your DNS provider. Cloudflare support currently provided.

Installation
------------

Run:

    $ python setup.py install

Usage
-----

``namesync --help``::

    usage: namesync [-h] [-d DATA_DIR] [-r] [-z ZONE] [-t] records

    positional arguments:
      records

    optional arguments:
      -h, --help            show this help message and exit
      -d DATA_DIR, --data-dir DATA_DIR
      -r, --remove-cache
      -z ZONE, --zone ZONE
      -t, --dry-run

Basic Usage
-----------

1. Create a file with the name or your domain::
    
    $ touch example.com

2. Enter one record per line with the following format::
   
   <record-type> <name> <value>

For example::

    A       *       10.10.10.10
    A       .       10.10.10.10
    A       test    10.10.10.11
    CNAME   mail    ghs.googlehosted.com
    MX      .       aspmx.l.google.com

If the value contains spaces, quote it::

    TXT   .         "v=spf1 a include:amazonses.com include:_spf.google.com ~all"
    
3. Perform a dry run to see what will happen::

   $ namesync --dry-run example.com

4. If everything looks good, sync for real::

   $ namesync example.com