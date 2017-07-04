# mystore
**Magento 2 Learning Centre**

> Steps to Install Magento 2 with Composer

**1. Install Composer**

You can skip this step if you have Composer already installed. Windows users have an installer available.

  ```curl -sS https://getcomposer.org/installer | php```

1.1 Make Composer Globally Available

If you wish, you can additionally install Composer globally so you don’t have to type ```php/path/to/composer.phar``` every time. The Windows installer will automatically set up the PATH system variable.

```mv composer.phar /usr/local/bin/composer```

**2. Download Magento 2**

Run the following command in root directory.

```composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition .```

**3. Set Up Permissions**

After all the dependencies are retrieved, you should set the correct permissions on the entire Magento 2 installation directory. The official documentation recommends chmod’ing all directories to 700 and all files to a level of 600:

```find . -type d -exec chmod 700 {} \; && find . -type f -exec chmod 600 {} \;```

In case you are still facing problems, you are probably logged in under a different user and have to give ownership of the installation directory to the web server user.

**4. Create The Database**

Given that you already have a MySQL user with the correct permissions, then create an empty database to work with. If you want to, you can also use an existing database and pick a table prefix during the installation process, but that’s not something a lot of people do.

``` echo "CREATE DATABASE my_dbname" | mysql -u[mysqluser] -p ```

**5. Install Magento 2**

That’s about it! You can now follow the installation wizard or use the command line.

**5.1 Installation Wizard**

Just fire up the browser, navigate to the host where you installed Magento 2 and if everything went correct, you should be redirected to the setup tool.

**5.2 Command Line Installer**

Magento 2 ships with a command line installer and can be invoked as followed:

```php bin/magento setup:install --base-url=http://mystore.dev/ --db-host=localhost --db-name=my_db_name --db-user=root --db-password=my_passw0rd  --admin-firstname=MyName --admin-lastname=My_lastname --admin-email=my@email.com --admin-user=mandla --admin-password=My_password --language=en_US --backend-frontname=admin --use-sample-data --magento-init-params=“MAGE_MODE=developer”```

The above command should be edited to your needs and executed from the Magento 2 root directory. What follows, is a bit of scrolling text and if everything went correct, you are informed that the installation has been completed.


