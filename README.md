# Scotty Shih-tzu

Restfull API built with Haskell, Scotty, mysql-haskell.

![Shih Tzu](https://user-images.githubusercontent.com/33439268/77206142-a2fcb600-6b39-11ea-96a6-461fb3525ed8.jpg)

## Requirements

- stack
- MySQL (@5.7)

## Setup DB (MySQL)

Create database.

```
mysql> create database shih_tzu;
```

Create table below.

```
$ mysql --version
mysql  Ver 14.14 Distrib 5.7.25, for osx10.14 (x86_64) using  EditLine wrapper
$ mysql ...login...
mysql> show create table users \G;
*************************** 1. row ***************************
       Table: users
Create Table: CREATE TABLE `users` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(20) NOT NULL,
  `password` varchar(255) DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `name` (`name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4

mysql> show create table dogs \G;
*************************** 1. row ***************************
       Table: dogs
Create Table: CREATE TABLE `dogs` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `name` varchar(20) NOT NULL,
  `bread` varchar(20) NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `owner_id` int(11) NOT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `name` (`name`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4

mysql> show create table photos \G;
*************************** 1. row ***************************
       Table: photos
Create Table: CREATE TABLE `photos` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `user_id` int(11) NOT NULL,
  `dog_id` int(11) NOT NULL,
  `url` varchar(255) NOT NULL,
  `title` varchar(20) NOT NULL,
  `created_at` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,
  PRIMARY KEY (`id`),
  UNIQUE KEY `url` (`url`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4
```

Finaly, insert record you like.

## Download & Boot run

First, fork this repository. Then

```
git clone https://github.com/{your_github_account}/scotty-shih-tzu.git
cd scotty-shih-tzu
stack setup        # this may take so long time.
stack run
```
In this way, you shoud be able to access below

- GET  http://localhost:3000
- GET  http://localhost:3000/users/:uid
- GET  http://localhost:3000/dogs/:did
- POST http://localhost:3000/dogs
- GET  http://localhost:3000/users/:uid/photos
- GET  http://localhost:3000/dogs/:did/photos
- POST http://localhost:3000/photos
