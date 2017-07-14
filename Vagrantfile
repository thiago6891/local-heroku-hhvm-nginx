Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest: 5000, host: 5000
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y nginx
	  apt-get install -y hhvm
	  apt-get install -y unzip zip
	  php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    php composer-setup.php
    php -r "unlink('composer-setup.php');"
	  mv composer.phar /usr/local/bin/composer
	  wget -qO- https://cli-assets.heroku.com/install-ubuntu.sh | sh
	  mv /vagrant/nginx.conf /etc/nginx/nginx.conf
  SHELL
end