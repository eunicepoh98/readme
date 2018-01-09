# Ruby on Rails

Installation
- [Ruby](https://rubyinstaller.org/downloads/)
- [PostgreSQL](https://www.postgresql.org/download/)

Install Rails by running
> gem install rails

## 1. Command Line Basics

Install the gems needed to run the application
> bundle install

### 1.1 rails new
To create a new application run:
> rails new `app_name`

To set postgresql as the database for the application run:
> rails new app_name `-d postgresql`

alternatively, you can use the [rails composer](https://github.com/RailsApps/rails-composer) to create an application with a starter template
> rails new app_name -m https://raw.github.com/RailsApps/rails-composer/master/composer.rb

### 1.2 rails server
the command below launches a web server named Puma which comes bundled with Rails. 
> rails s

Your Rails server will be listening on [http://localhost:3000](http://localhost:3000)

you can also bind it to your IP adress by running
> rails s `-b 192.168.1.2`

### 1.3 rails generate
rails generate command generates boilerplate code necessary for the app to work saving time

Generating Controller:

running the command below will create a controller file, view file, functional test file, a helper for the view, a JavaScript file and stylesheet file
> rails g controller `NAME`

Generating Data Models:
> rails g model `NAME`

Generate Sccaffold:
Scaffold in Rails is a full set of model, database migration for model, controller to manipulate it, views to view the manipulated data and a test suite for each of the above.
> rails generate scaffold `NAME` *attribute:type*

### 1.4 rails console
console commands lets you interact with your Rails application from the command line. Useful for changing data server-side
> rails console

### 1.5 rails routes
rails routes will list all your defined routes, useful for tracking down route problems in app or giving good overview of the URLs in an application
> rails routes

### 1.6 rails db
commands to setup database or perform migrations
> rails db:migrate, rails db:setup

## 2. Getting Started
Below are some useful tutorials to get started on learning Ruby on Rails.

2.1 Rails Basic (http://guides.rubyonrails.org/getting_started.html)

2.2 Simple CMS Blog with some commonly used gems

1. [Part 1](https://scotch.io/tutorials/build-a-blog-with-ruby-on-rails-part-1) (CRUD, Forms, Bootstrap)

2. [Part 2](https://scotch.io/tutorials/build-a-blog-with-ruby-on-rails-part-2) (Authentication, Validation, Image Uploading)


## 3. Gems
List of used/useful gems

### 3.1 Authentication and Authorisation
#### Authentication

3.1.1 [Devise](https://github.com/plataformatec/devise)

3.1.2 [Authenticate](https://github.com/tomichj/authenticate)

#### Authorisation

3.1.3 [Cancancan](https://github.com/CanCanCommunity/cancancan)

#### Tutorials
Devise with cancancan- [link](https://hibbard.eu/authentication-with-devise-and-cancancan-in-rails-4-2/)

Devise cancancan (3 roles) - [link](http://codepany.com/blog/rails-5-user-accounts-with-3-types-of-roles-devise-rails_admin-cancancan/)

### 3.2 Admin Interface
Uses Domain Specific Language to build the backend

3.2.1 [ActiveAdmin](https://github.com/activeadmin/activeadmin)

Basic Usage: https://www.youtube.com/watch?v=NJYtzznKrg0

3.2.2 [RailsAdmin](https://github.com/sferik/rails_admin)

Tutorial: https://www.youtube.com/watch?v=agzm_O-pZFE

### 3.3 Backend, API
#### Documentation Tool
3.3.1 [api-pie](https://github.com/Apipie/apipie-rails)

Tutorial - [link](http://tech.eshaiju.in/blog/2015/01/09/apipie-rails-rails-api-documentation-tool/)

#### CORS
3.3.2 [Rack CORS](https://github.com/cyu/rack-cors)

#### Displaying Charts

3.3.3 [Chartkick](https://github.com/ankane/chartkick)

3.3.4 [Groupdate](https://github.com/ankane/groupdate)

#### Tutorial
API in Rails - [link](https://www.kollegorna.se/en/2015/04/build-an-api-now/)

### 3.4 Frontend
3.4.1 [jquery](https://github.com/rails/jquery-rails)

3.4.2 [Font-Awesome](https://github.com/FortAwesome/font-awesome-sass)
- Font-awesome icons [here](http://fontawesome.io/)

3.4.3 [momentjs](https://github.com/derekprior/momentjs-rails)

3.4.4 [flag-icons-rails](https://github.com/evgenygarl/flag-icons-rails)

3.4.5 [country_list](https://github.com/michaelkoper/country_list)

### 3.5 Image Uploading

3.5.1 [Carrierwave](https://github.com/carrierwaveuploader/carrierwave)

With S3: http://kerrizor.com/blog/2014/04/13/carrierwave-and-s3

### 3.6 Others

3.6.1 [Figaro](https://github.com/laserlemon/figaro)

3.6.2 [Rails Bootstrap Forms](https://github.com/bootstrap-ruby/rails-bootstrap-forms)

3.6.3 [Framework7 with Rails](https://github.com/pracstrat/framework7_rails)

3.6.4 [maybe](https://github.com/bhb/maybe)
- for treating nil and non-nil objects in a similar manner

3.6.5 [device_detector](https://github.com/podigee/device_detector)

3.6.6 [rest-client](https://github.com/rest-client/rest-client)

3.6.7 [aws-sdk](https://github.com/aws/aws-sdk-ruby)

## 4. Active Record 
### 4.1 Validation
http://guides.rubyonrails.org/active_record_validations.html

### 4.2 Association

#### 4.2.1 Many-to-Many relationships

##### HMT (has_many :through)
- http://www.mozartreina.com/m-to-m-with-rails-2.html

##### HABTM (has_and_belongs_to_many)
- http://www.mozartreina.com/m-to-m-with-rails.html

When to use:
- https://www.sitepoint.com/master-many-to-many-associations-with-activerecord/
- http://guides.rubyonrails.org/association_basics.html#choosing-between-has-many-through-and-has-and-belongs-to-many

Examples:
- https://www.rubyplus.com/articles/3451-Has-Many-Through-and-Has-and-Belongs-to-Many-in-Rails-5
- https://coderwall.com/p/i4c8mg/has_and_belongs_to_many-habtm-associations-in-rails-4

#### 4.2.2 Polymorphic Associations
A model belonging to more than one other model
- http://guides.rubyonrails.org/association_basics.html#polymorphic-associations
- https://gorails.com/episodes/comments-with-polymorphic-associations?autoplay=1

## 5. Routing

Scope vs Namespace - [link](https://devblast.com/b/rails-5-routes-scope-vs-namespace)

## 6. Front-end
Bootstrap 3:
https://getbootstrap.com/docs/3.3/

Bootstrap 4:
https://getbootstrap.com/docs/4.0/getting-started/introduction/

Material Design:
https://material.io/components/

React with Rails: https://medium.com/superhighfives/a-top-shelf-web-stack-rails-5-api-activeadmin-create-react-app-de5481b7ec0b

Animate.css: https://daneden.github.io/animate.css/

Wow.js: http://mynameismatthieu.com/WOW/

Google Map Javascript: [API](https://developers.google.com/maps/documentation/javascript/tutorial)

## 7.

## 8. MISC.
### 8.1 Image resizing
External installation needed for using image resizing gems

ImageMagick (windows) - [download](https://www.imagemagick.org/script/download.php#windows)

GraphicMagick ([windows](http://www.graphicsmagick.org/INSTALL-windows.html)) - [download](ftp://ftp.graphicsmagick.org/pub/GraphicsMagick/windows/)

### 8.2 Heroku

First time:
> heroku rake db:migrate


## 9. Weird Errors

### 9.1 Postgres Service gone/not starting
> pg_ctl.exe register -N postgres -D "PGDATADIR"