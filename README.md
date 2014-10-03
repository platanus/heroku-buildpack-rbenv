## heroku-buildpack-rbenv

Use rbenv with [heroku-buildpack-ruby](https://github.com/Crowdflower/herok-buildpack-ruby) using buildpack layering with [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi).

# Usage:

Point the ```BUILDPACK_URL``` to ddollar's [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi):

    $ heroku config:add BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git

Alternatively, use [dotenv](https://github.com/bkeepers/dotenv) and include ```BUILDPACK_URL``` in your .env file:

    $ grep BUILDPACK_URL .env || echo BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git >> .env

Add this repository to your .buildpacks file:

    https://github.com/CrowdFlower/heroku-buildpack-rbenv.git
    https://github.com/CrowdFlower/heroku-buildpack-ruby.git

# Implementation:

This installs rbenv and prepares .profile.d to source it.

This also detects the version of ruby mentioned in your .ruby-version file and ruby directive in your Gemfile, and does a rbenv install of those ruby versions.

This only provides a ruby runtime, it does not prepare a web server, run a Procfile, or provide any other features necessary for full buildpack functionality. This is meant to be layered in before heroku-buildpack-ruby using herok-buildpack-multi.


