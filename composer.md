## 安装
1. wget https://getcomposer.org/composer.phar
2. mv composer.phar composer
3. chmod +x composer
4. sudo mv composer /usr/local/bin

1. sudo apt update
2. sudo apt install wget php-cli php-zip unzip
3. wget -O composer-setup.php https://getcomposer.org/installer
4. sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

### linux 安装
1. php -r "copy('https://install.phpcomposer.com/2.installer', 'composer-setup.php');"
2. php composer-setup.php
3. mv composer.phar /usr/local/bin/composer
4. composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/ 切换镜像
5. composer selfupdate

### 切换镜像
composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

## 使用
take test
compser require
```
<?php
    require __DIR__ . '/vendor/autoload.php';

    use Carbon\Carbon;

    printf("Now: %s", Carbon::now());
```

## 命令
1. composer self-update 更新composer到最新
2. composer require package-name 安装包 可以指定版本，如： composer require new/package ~2.5
3. composer install package-name 如有 composer.lock 文件，直接安装，否则从 composer.json 安装最新扩展包和依赖；***不常用***
4. composer update package-name  从 composer.json 安装最新扩展包和依赖 ***不常用***
5. composer remove package-name 删除包
6. composer search package-name 寻找包


