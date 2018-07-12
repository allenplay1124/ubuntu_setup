# ubuntu 伺服器安裝筆記

1. 系統更新

  ```bash
  sudo apt-get update           //更新套件資料庫
  sudo apt-get -y upgrade       //更新
  sudo apt-get -y dist-upgrade  //如果有相依性更新，會嚐試安裝或更新，風險略高
  sudo apt-get -y autoremove    //清除無用套件
  sudo apt-get -y autoclean     //清除快取
  ```

2. 安裝常用工具

  ```bash
  sudo apt-get install -y wget curl build-essential openssl libssl-dev
  sudo apt-get install -y libcurl4-gnutls-dev libexpat1-dev gettext libz-dev
  sudo apt-get install -y software-properties-common
  sudo apt-get install -y  python g++ make
  sudo apt-get install -y python-software-properties
  ```

3. 解決 Linux Mint 字體問題

  ```bash
  sudo apt-get -y remove fonts-arphic-ukai fonts-arphic-uming
  ```

4. 安裝 nginx

  ```bash
  wget http://nginx.org/keys/nginx_signing.key
  sudo apt-key add nginx_signing.key
  sudo echo deb http://nginx.org/packages/mainline/ubuntu/ ${codename} nginx > /etc/apt/sources.list.d/nginx.list
  sudo echo deb-src http://nginx.org/packages/mainline/ubuntu/ ${codename} nginx >> /etc/apt/sources.list.d/nginx.list
  sudo apt-get update
  sudo apt-get -y install nginx
  sudo service nginx start              //啟用服務
  sudo service nginx status             //查詢nginx狀態
  ```

  `codename` 為 Ubuntu 版本代號，可以參考 <https://nginx.org/en/linux_packages.html#distributions>

5. 安裝 mysql

  ```bash
  sudo apt-get update
  sudo apt-get -y install mysql-server  //安裝 mysql-server
  sudo mysql_secure_installation        //設定root密碼
  sudo service mysql start              //啟用服務
  sudo service mysql status             //查詢mysql狀態
  ```

6. 安裝 php

  ```bash
  sudo add-apt-repository -y ppa:ondrej/php
  sudo apt-get update
  ## 安裝 php70
  sudo apt-get install -y php7.0 php7.0-fpm libapache2-mod-php7.0 php7.0 php7.0-common php7.0-gd php7.0-mysql php7.0-cli php7.0-mcrypt php7.0-curl php7.0-intl php7.0-xsl php7.0-mbstring php7.0-zip php7.0-bcmath
  ## 安裝 php56
  sudo apt-get install -y php5.6 php5.6-fpm php5.6-common php5.6-mcrypt php5.6-gmp php5.6-curl php5.6-cli php5.6-mysql php5.6-gd php5.6-intl php5.6-xsl php5.6-mbstring php5.6-xml

  sudo apt-get install -y php-mongodb php-redis php-geoip php-memcache
  ## 啟用服務
  sudo service php5.6-fpm start
  sudo service php7.0-fpm start
  ```

  修改 `cli` 預設的 php 版本

  ```bash
  sudo update-alternatives --set php /usr/bin/php5.6
  sudo update-alternatives --set php /usr/bin/php7.0
  ```

7. 安裝 git

  ```bash
  sudo add-apt-repository ppa:git-core/candidate
  sudo apt-get update
  sudo apt-get install git
  ```

8. 安裝 `composer`

  ```bash
  php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
  php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
  php composer-setup.php --install-dir=/usr/bin --filename=composer
  php -r "unlink('composer-setup.php');"
  ```

9. 安裝 nodejs、npm

  ```bash
  ## 安裝 nvm
  curl https://raw.githubusercontent.com/creationix/nvm/v0.16.1/install.sh | sh
  ## 更新環境變數
  source ~/.profile
  ## 查詢可安裝的版本號
  nvm ls-remote

  ## 安裝 nodejs、npm
  nvm install v8.6.0

  ## 查詢 nodejs、npm 版本號
  node -v
  npm -v
  ```

10. 安裝 yarn

  ```bash
  ## 安裝
  sudo npm install -g yarn
  ## 查看版本
  yarn -v
  ```

11. 安裝 gulp

  ```bash
  sudo npm install -g gulp
  ## 查看版本
  gulp -v
  ```
