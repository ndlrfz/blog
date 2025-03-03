+++
date = '2025-03-04T05:10:43+07:00'
draft = false
title = 'How to Install PHP OCI8 (Oracle Instant Client) Module on Debian/Ubuntu'
+++

In this guide, I will show you how to install PHP OCI8 (Oracle Instant Client) on Debian 12 server.

In this example, I've **PHP 8.4** installed. Let's begin.

- Dowload [Oracle Instant Client libraries](https://www.oracle.com/database/technologies/instant-client/downloads.html) to your system. In this example, I will use `instantclient-basic-linux.x64-23.7.0.25.01.zip` and `instantclient-sdk-linux.x64-23.7.0.25.01.zip`.

Make sure to use the correct version based on your _GLIBC_ version. Check the _glibc_ version with the `ldd` command.

```bash
sudo ldd --version
```

- Extract Oracle Instant Client Libraries

```bash
sudo apt install unzip -y
unzip instantclient-basic-linux.x64-23.7.0.25.01.zip
unzip instantclient-sdk-linux.x64-23.7.0.25.01.zip
```

- Move the Oracle Instant Client libraries to the correct path.

```bash
mkdir -p /usr/local/lib/oracle/
mv instantclient_23_7 /usr/local/lib/oracle/
ln -s /usr/local/lib/oracle/instantclient_23_7 /usr/local/lib/oracle/instantclient

cd /usr/local/lib/oracle
find instantclient_23_7 -type f -exec chmod 644 {} +
find instantclient_23_7 -type d -exec chmod 755 {} +
```

- Download PHP OCI8 module and compile.

```bash
sudo apt install php8.4-dev

cd /usr/src/
wget https://pecl.php.net/get/oci8-3.4.0.tgz
tar xzf oci8-3.4.0.tgz

cd oci8-3.4.0

phpize8.4
./configure --with-oci8=instantclient,/usr/local/lib/oracle/instantclient --with-php-config=/usr/bin/php-config8.4
make
```

- Install PHP OCI8 module.

```bash
make install
chmod 644 /usr/lib/php/20240924/oci8.so

echo '; priority=10' > /etc/php/8.4/mods-available/oci8.ini
echo 'extension=oci8.so' >> /etc/php/8.4/mods-available/oci8.ini

chmod 644 /etc/php/8.4/mods-available/oci8.ini
phpenmod -v 8.4 oci8
```

- Adding new library path for Oracle Instant Client libraries.

```bash
vim /etc/ld.so.conf.d/xx_php_oci8.conf
```

```ini
# path to oracle instant client directory
/usr/local/lib/oracle/instantclient
```

```bash
sudo ldconfig
```

- Restart Apache and verify PHP module.

```bash
sudo systemctl restart apache2
php -m | grep oci
```

Output:

```sh
oci8
```

Thanks.
