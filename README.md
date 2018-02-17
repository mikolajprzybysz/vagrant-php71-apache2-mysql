# Vagrant with php71 apache24 mysql57
This project is suppose to be founding piece for any PHP service you quickly want to have up and runnig 
with a Vagrant image. The idea is to have designated environment for each service that can be independently deployable and run.

Apps shipped along:
* php 7.1
* apache 2.4
* mysql 5.7

Further features:
* bootstrap apache2 config
* bootstrap database structure and content on vagrant up

## How to start
* Currently you need to either copy all the files or start your project from the fork of this
* Add database schema and sample data to [database/data.sql](database/data.sql)
* Run `vagrant up` this will create virtual machine that will try to fix itself to port 80
* Build your project, create `index.php` in [public/](public/) directory
* Test your project by acccessing [http://localhost/index.html](http://localhost/index.html)
* After you are done simply `vagrant destroy`
* Next time you will want to work on the project simply `vagrant up` again and you will get fresh database and env without any modifications. In case you want to change enviornment make changes in [Vagrantfile](Vagrantfile) directly in order to have immutable infrastructure

## Roadmap
* Be able to load this as dependency to your project via composer
* Add support for https
