Heroku buildpack: Python, Numpy, and Scipy
====================================================

This is a custom [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks)
for Python apps that use NumPy and/or SciPy, powered by [pip](http://www.pip-installer.org/).

Note: This buildpack currently only supports the `cedar-14` stack. If you 
need binaries for the original `cedar` stack, check out 
[thenovices' repo](https://github.com/thenovices/heroku-buildpack-scipy)

Please open a GitHub for any problems encountered or feature requests.

Details
-------

This buildpack currently supports:

NumPy:
  * 1.9.1

SciPy:
  * 0.14.0 (compiled against NumPy 1.9.1)

This package will also install compiled runtime libraries for BLAS, LAPACK,
ATLAS, and Fortran, which are needed by NumPy and SciPy at runtime.

Usage
-----
For a new app:

    heroku create --buildpack https://github.com/andrewychoi/heroku-buildpack-scipy

For an existing app:

    heroku config:set BUILDPACK_URL=https://github.com/andrewychoi/heroku-buildpack-scipy

You must specify your exact desired version in `requirements.txt` (e.g.,
`numpy==1.9.0`). If no version is specified, the latest version available will
be used. At this time, this buildpack does not support requirements of the
form `numpy>=1.8`.

Demo
----

    $ mkdir testheroku
    $ cd testheroku
    $ git init
    $ heroku create --buildpack https://github.com/andrewychoi/heroku-buildpack-scipy
    $ echo -e "numpy==1.8.1\nscipy==0.14.0" > requirements.txt
    $ git add requirements.txt
    $ git commit -m 'Added requirements'
    $ git push heroku master


Acknowledgments
---------------

This fork is taken from @thenovices: thanks to him and his acknowledgements: 
@dbrgn, @wyn, and others for
setting up a lot of the code here.
