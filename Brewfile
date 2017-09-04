
# ---------------------------------- TAPS --------------------------------------

tap 'Yleisradio/homebrew-terraforms'
tap 'universal-ctags/universal-ctags'
tap 'homebrew/services'

# --------------------------------- BREWS --------------------------------------

# ELIXIR
brew 'elixir'

# ELM
brew 'elm'
brew 'elm-format'

# PYTHON
brew 'python'
brew 'python3'
brew 'pip'

# GIT
brew 'git'
# GitHub
brew 'hub'

# ZSH
brew 'zsh'
brew 'zsh-syntax-highlighting'

# HEROKU
brew 'heroku'
brew 'hostess'

# IMAGE MANIPULATION
brew 'imagemagick@6'

# RAILS DEV
brew 'openssl'
brew 'libyaml' # should come after openssl
brew 'node'
brew 'phantomjs'
brew 'postgresql'
brew 'rbenv'
brew 'ruby-build'
brew 'openssl'

# DATABASES
brew 'postgres', restart_service: :changed
brew 'redis',    restart_service: :changed

# CTAGS
brew 'universal-ctags', args: ['HEAD']

# ---------------------------------- CASK --------------------------------------

cask 'ccmenu'
cask 'docker'

# Core Apps
cask_args appdir: '/Applications'

cask 'alfred'
cask 'dropbox'
cask 'little-snitch'
cask 'iterm2'
cask 'java' unless system '/usr/libexec/java_home --failfast'

# ORGANISATION
cask 'wunderlist'
cask 'puush'
cask 'slack'

# DEVELOPMENT
cask 'atom'
cask 'macvim'
cask 'postico'

# DAY 2 DAY
cask 'google-chrome'
cask 'spotify'
cask 'spotify-notifications'
