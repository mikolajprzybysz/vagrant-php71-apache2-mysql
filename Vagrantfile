# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest: 80, host: 80, host_ip: "127.0.0.1"
  config.vm.provision :shell, inline: <<-SHELL
    # install php7.1
    sudo apt install -y python-software-properties
    sudo add-apt-repository -y ppa:ondrej/php
    sudo apt update -y
    sudo apt install -y php7.1 libapache2-mod-php7.1 php7.1-xml

    # install and config apache2
    sudo apt install -y apache2
    sudo ln -s /vagrant/apache2/sites-available/service.conf /etc/apache2/sites-available/service.conf
    sudo a2dissite 000-default.conf
    sudo a2ensite service.conf
    sudo a2enmod rewrite
    sudo service apache2 restart

    # install mysql
    sudo debconf-set-selections <<< 'mysql-server mysql-server/root_password password root123'
    sudo debconf-set-selections <<< 'mysql-server mysql-server/root_password_again password root123'
    sudo apt -y install mysql-server

    # bootstrap mysql
    mysql -uroot -proot123 < /vagrant/database/data.sql
  SHELL
end
