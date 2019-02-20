chitter [![Build Status](https://travis-ci.org/tomasdoh/chitter.svg?branch=master)](https://travis-ci.org/tomasdoh/chitter)
=================

Sign up to start peeping on [*_chitter_*](https://chitterr.herokuapp.com/peeps), a Twitter clone built using Sinatra, Datamapper and PostgreSQL, and tested with RSpec and Capybara.

### Screenshots

![chitter homepage screenshot](/public/images/homepage.png)
![chitter peeps screenshot](/public/images/peeps.png)
![chitter log-in screenshot](/public/images/log-in.png)
![chitter sign-up screenshot](/public/images/sign-up.png)

### User stories
```
As a user
So that I can let people know what I am doing  
I want to post a message (peep) to chitter

As a user
So that I can see what others are saying  
I want to see all peeps in reverse chronological order

As a user
So that I can better appreciate the context of a peep
I want to see the time at which it was made

As a user
So that I can post messages on chitter as me
I want to sign up for chitter

As a user
So that only I can post messages on chitter as me
I want to log in to chitter

As a user
So that I can avoid others posting messages on chitter as me
I want to log out of chitter

```
### Getting started

Download or clone the repository to your local machine. Change into the `chitter` directory and run `bundle install` to make sure you have all the necessary dependencies installed.

Then type the following commands into the terminal to create a database and run a local server:
```
$ createdb chitter
$ rackup
```
You should then be able to access chitter on `http://localhost:9292`

### Testing

The application has been tested using RSpec and Capybara and has 100% coverage.

To run the tests locally:
```
cd chitter
bundle install
rspec
```

### My approach

I decided to use Datamapper ORM for this project, both so that I could understand how an ORM design pattern works in practice and so that the code required to interact with database could be kept to a minimum.

Some of the challenges I encountered:

- It was difficult to get all of the dependencies working together. The default json gem (2.1) was conflicting with DataMapper 1.2. In the end I had to use json 1.8.6.
- Initially I wasn't using a test database and instead used Database Cleaner to ensure any test data was removed after each test. I've now implemented the use of a test database along with Database Cleaner.
- I didn't use unit tests for the User and Peep classes during the development of the application as I wasn't sure how to test DataMapper. I've since used some [specific RSpec matchers](https://github.com/greyblake/dm-rspec) for DataMapper.
- I found it challenging to get the authentication system working with an encrypted password without any clear guidance on how to implement this using DataMapper. I did find a solution in the end and the system now works consistently.
