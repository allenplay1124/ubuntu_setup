# MacOS 裝機筆記

本篇介紹在 Mac OS 環境下，安裝  `php`、`nginx`、`mysql`及一些常用的開發工具

## Homebrew 安裝

`homebrew` 是 Mac OS 套件管理包，與 `CentOS` 的 `yum` 或 `Ubuntu` 的 `apt` 功能相同。

### `homebrew` 安裝前需要先裝裝 xcode

```bash
xcode-select --install
```

### `homebrew` 安裝

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### `nginx` 安裝

* 安裝指令
```bash
brew install nginx
```
* 啟用指令
```bash
brew services start nginx
```

### `mariadb` 安裝

* 安裝指令
```bash
brew install maraidb
```
* 啟用指令
```bash
brew serices start mysql
```
* 設定 mysql root 密碼
```bash
mysqladmin -u root password '密碼'
```
* 設定 mysql root 帳密及安全設定 **推薦**
```bash
mysql_secure_installation
```
主要設定內容：
  - 設定`root`密碼
  - 刪除匿名連線權限
  - 刪除 `test` 資料庫
  - 刪除 `root` 遠端連線的權限


* 推薦 Mysql Client [Sequel Pro](https://www.sequelpro.com/)

### `php` 安裝

* 安裝 php7.1
```bash
brew install php@7.1
```
* 安裝 php7.0
```bash
brew install php@7.0
```
* 安裝 php5.6
```bash
brew install php@5.6
```

### php版本切換
* 安裝`brew-php-switcher`
```bash
brew install brew-php-switcher
```
* 版本切換
```bash
brew-php-switcher (版本號)
```
***P.S必需有安裝相應的版本，才能切換***

### brew services

* 查詢所有務狀態
```bash
brew services list
```
顯示如下：
```bash
Name    Status  User   Plist
mariadb started jailin /Users/jailin/Library/LaunchAgents/homebrew.mxcl.mariadb.plist
nginx   started jailin /Users/jailin/Library/LaunchAgents/homebrew.mxcl.nginx.plist
php     stopped        
php@5.6 stopped        
php@7.0 stopped        
php@7.1 started jailin /Users/jailin/Library/LaunchAgents/homebrew.mxcl.php@7.1.plist
```

* 開啟服務
```bash
brew services start (服務名稱)
```

* 停止服務
```bash
brew services stop (服務名稱)
```

* 重啟服務
```bash
brew services restart (服務名稱)
```
