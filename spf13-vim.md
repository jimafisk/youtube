### Download spf13
```
sudo apt-get update
sudo apt-get install git
curl http://j.mp/spf13-vim3 -L -o - | sh
```

### Download Tagbar
```
git clone git://github.com/majutsushi/tagbar ~/.vim/bundle/tagbar
sudo apt-get install exuberant-ctags
```

### Install VDebug using Vundle
Add to ~/.vimrc: `Bundle 'joonty/vdebug.git'`<br />
From the command line run: `vim +BundleInstall +qall`

### Download XDebug
```
sudo apt-get install php5-xdebug
sudo php5enmod xdebug
```

### Add to /etc/php5/apache2/php.ini for Vdebug
```
zend_extension=/usr/lib/php5/20121212/xdebug.so
xdebug.remote_autostart = On
xdebug.remote_enable = On
xdebug.remote_host = localhost
xdebug.remote_port = 9000
```

### Add to ~/.vimrc for Codesniffer
```
let g:syntastic_php_phpcs_args="--standard=Drupal --extensions=php,module,inc,install,test,profile,theme"
if has('statusline')
set laststatus=2
" Broken down into easily includeable segments
set statusline=%<%f\ " Filename
set statusline+=%w%h%m%r " Options
set statusline+=%{fugitive#statusline()} " Git Hotness
set statusline+=\ [%{&ff}/%Y] " filetype
set statusline+=\ [%{getcwd()}] " current dir
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*
let g:syntastic_enable_signs=1
set statusline+=%=%-14.(%l,%c%V%)\ %p%% " Right aligned file nav info
endif
```

### Add coding standard support
```
sudo apt-get install pear
sudo pear install PHP_codesniffer
```

### Setup Composer
```
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
```
Add the following to ~/.bashrc: `export PATH="$HOME/.composer/vendor/bin:$PATH"`
```
source ~/.bashrc
```

### Install Coder using Composer
```
composer global require drupal/coder
sudo phpcs --config-set installed_paths ~/.composer/vendor/drupal/coder/coder_sniffer
```

### Test codesniffer on the command line
```
phpcs --standard=Drupal --extensions=php,module,inc,install,test,profile,theme,js,css,info,txt,md /var/www/drupal-8.0.2/core/modules/block/block.module
```
