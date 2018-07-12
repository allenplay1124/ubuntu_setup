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

### `mysql` 安裝

* 安裝指令
```bash
brew install mysql
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
