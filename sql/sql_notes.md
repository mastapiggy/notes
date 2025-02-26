# SQL Notes

## Install mysql on ubuntu

sudo apt install mysql-server

sudo mysql

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'YourPassword';

sudo mysql_secure_installation


after installation:
mysql -u root -p
CREATE USER 'youruser' IDENTIFIED BY 'yourpassword';
GRANT ALL PRIVILEGES ON *.* TO 'youruser' WITH GRANT OPTION;
