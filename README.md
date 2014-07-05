[![Build Status](https://travis-ci.org/niteoweb/heroku-buildpack-lftp.svg?branch=master)](https://travis-ci.org/niteoweb/heroku-buildpack-lftp)

Heroku buildpack: lftp
=======================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks)
for adding lftp to your application.

Multipacks
----------

More likely, you'll want to use it as part of a larger project, which needs to use lftp. The easiest way to do this is with a [multipack](https://github.com/ddollar/heroku-buildpack-multi),
where this is just one of the buildpacks you'll be working with.

    $ cat .buildpacks
    git://github.com/heroku/heroku-buildpack-ruby.git
    git://github.com/niteoweb/heroku-buildpack-lftp.git

    $ heroku config:add BUILDPACK_URL=git://github.com/ddollar/heroku-buildpack-multi.git

This will bundle lftp into your instance without impacting your existing
system.


Develop
-------

    $ git clone http://github.com/niteoweb/heroku-buildpack-lftp.git
    $ cd heroku-buildpack-lftp

    $ heroku create -s cedar
    ...

    $ heroku plugins:install https://github.com/heroku/heroku-repo.git
    $ heroku plugins:install https://github.com/glenngillen/heroku-exit-status.git

    $ heroku config:add BUILDPACK_URL=http://github.com/kr/heroku-buildpack-inline.git
    ...

    $ git push heroku master
    ...

    $ heroku run "lftp -v"
    LFTP | Version 4.5.1 | Copyright (c) 1996-2014 Alexander V. Lukyanov
    ...
