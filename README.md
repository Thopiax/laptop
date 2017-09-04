Laptop
======

My version of the laptop script for setting up a macOS
laptop for web and mobile development. (Original by thoughtbot)

It can be run multiple times on the same machine safely.
It installs, upgrades, or skips packages
based on what is already installed on the machine.

Install
-------

Download the script:

```sh
curl --remote-name https://raw.githubusercontent.com/Thopiax/laptop/master/mac
```

Execute the downloaded script:

```sh
sh mac 2>&1 | tee ~/laptop.log
```

Development tools
---------------

macOS tools:

* [Homebrew] for managing operating system libraries.

[Homebrew]: http://brew.sh/

Unix tools:

* [Exuberant Ctags] for indexing files for vim tab completion
* [Git] for version control
* [OpenSSL] for Transport Layer Security (TLS)
* [OhMyZsh] as your shell

[Exuberant Ctags]: http://ctags.sourceforge.net/
[Git]: https://git-scm.com/
[OpenSSL]: https://www.openssl.org/
[Zsh]: https://github.com/robbyrussell/oh-my-zsh

VMs and Containers:

* [Docker] for easy containerisation

[Docker]: https://www.docker.com

Heroku tools:

* [Heroku CLI] for interacting with the Heroku API
* [Hostess] for managing the /etc/hosts file

[Heroku CLI]: https://devcenter.heroku.com/articles/heroku-cli
[Hostess]: https://github.com/cbednarski/hostess

GitHub tools:

* [Hub] for interacting with the GitHub API

[Hub]: http://hub.github.com/

Image tools:

* [ImageMagick] for cropping and resizing images

Testing tools:

* [Qt 5] for headless JavaScript testing via [Capybara Webkit]

[Qt 5]: http://qt-project.org/
[Capybara Webkit]: https://github.com/thoughtbot/capybara-webkit

Programming languages:

* [Elm] for JavaScript projects
* [Elixir] for functional & concurrent programming needs
* [Ruby] and [Python] for general development

Package managers, and configuration:

* [Bundler] for managing Ruby libraries
* [Node.js] and [NPM], for running apps and installing JavaScript packages
* [Rbenv] for managing versions of Ruby
* [Ruby Build] for installing Rubies
* [Yarn] for managing JavaScript packages

[Bundler]: http://bundler.io/
[ImageMagick]: http://www.imagemagick.org/
[Node.js]: http://nodejs.org/
[NPM]: https://www.npmjs.org/
[Rbenv]: https://github.com/sstephenson/rbenv
[Ruby Build]: https://github.com/sstephenson/ruby-build
[Ruby]: https://www.ruby-lang.org/en/
[Elm]: http://elm-lang.org
[Elixir]: https://elixir-lang.org
[Python]: https://www.python.org
[Yarn]: https://yarnpkg.com/en/

Databases:

* [Postgres] for storing relational data
* [Redis] for storing key-value data

[Postgres]: http://www.postgresql.org/
[Redis]: http://redis.io/

Applications
------------

Core Apps:

* [Alfred] for a better spotlight search
* [Dropbox] for great and easy cloud storage
* [Little Snitch] for stopping any unwanted connections
* [Java] just in case

Development:

* [iTerm2] for a better terminal
* [Atom] for fully customisable editor
* [MacVIm] for a more adapt quick editor
* [Postico] for simpler database handling

Day2Day:

* [Google Chrome] when Safari f*cks up
* [Spotify] for tunes

[Alfred]: https://www.alfredapp.com
[Dropbox]: https://www.dropbox.com/
[MacVIm]: http://macvim-dev.github.io/macvim
[Postico]: https://eggerapps.at/postico/
[iTerm2]: https://www.iterm2.com
[Atom]: https://atom.io
[Little Snitch]: https://www.obdev.at/products/littlesnitch/index.html
[Java]: https://www.java.com/en/
[Google Chrome]: https://www.google.com/chrome/index.html
[Spotify]: https://www.spotify.com/us/

It should take less than 15 minutes to install (depends on your machine).

Customize in `~/.laptop.local`
------------------------------

Your `~/.laptop.local` is run at the end of the Laptop script.
Put your customizations there.
For example:

```sh
#!/bin/sh

brew bundle --file=- <<EOF
brew "Caskroom/cask/dockertoolbox"
brew "go"
brew "ngrok"
brew "watch"
EOF

default_docker_machine() {
  docker-machine ls | grep -Fq "default"
}

if ! default_docker_machine; then
  docker-machine create --driver virtualbox default
fi

default_docker_machine_running() {
  default_docker_machine | grep -Fq "Running"
}

if ! default_docker_machine_running; then
  docker-machine start default
fi

fancy_echo "Cleaning up old Homebrew formulae ..."
brew cleanup
brew cask cleanup

if [ -r "$HOME/.rcrc" ]; then
  fancy_echo "Updating dotfiles ..."
  rcup
fi
```

Write your customizations such that they can be run safely more than once.
See the `mac` script for examples.

Laptop functions such as `fancy_echo` and
`gem_install_or_update`
can be used in your `~/.laptop.local`.

See the [wiki](https://github.com/thoughtbot/laptop/wiki)
for more customization examples.

License
-------

Laptop is © 2011-2017 thoughtbot, inc.
It is free software,
and may be redistributed under the terms specified in the [LICENSE] file.

[LICENSE]: LICENSE
