## Mac OS下安装及配置MySQL5.7

### 安装包

- 下载 MySQL5.7 应用包

  下载页: https://downloads.mysql.com/archives/community/

### 配置及安装

- 点击 MySQL 软件包安装

- 记住默认密码

- 第一次进入要求修改密码

  ```mysql
  use mysql;
  
  update user set authentication_string=password("root") where user="root";
  
  flush privileges;
  ```

- 配置环境变量

  ```bash
  sudo vim ~/.bash_profile
  
  #MYSQL
  export PATH=/usr/local/mysql/bin:$PATH
  
  sudo source ~/.bash_profile
  ```

### 系统变量

- 修改变量

  ```bash
  $ mysql --verbose --help | grep my.cnf
  
  /etc/my.cnf /etc/mysql/my.cnf /usr/local/mysql/etc/my.cnf ~/.my.cnf
  
  $ sudo vim /etc/my.cnf
  
  [mysqld]
  explicit_defaults_for_timestamp = ON
  
  sql_mode=STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION
  ```

* 服务关闭

  在 Mac OS 系统设置中，手动开启关闭 MySQL 服务。