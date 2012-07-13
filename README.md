# HttpAcceptLanguage

A small effort in making a plugin which helps you detect the users preferred language, as sent by the HTTP header.

## Features

* Splits the http-header into languages specified by the user
* Returns empty array if header is illformed.
* Corrects case to xx-XX
* Sorted by priority given, as much as possible.
* Gives you the most important language
* Gives compatible languages

See also: http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html

## Example

``` ruby
class SomeController < ApplicationController

  def some_action

    request.user_preferred_languages # => [ 'nl-NL', 'nl-BE', 'nl', 'en-US', 'en' ]
    available = %w{en en-US nl-BE}
    request.preferred_language_from(available) # => 'nl-BE'

    request.user_preferred_languages # => [ 'en-GB']
    available = %w{en-US}
    request.compatible_language_from(available) # => 'en-US'

  end

end
```

## Installation


### Without Bundler

Install the gem `http_accept_language`, require it in your Rails app.

### With Bundler

Add the gem to your Gemfile:

``` ruby
gem 'http_accept_language'
```

Run `bundle install` to install it.

## Changelog

* 2012-07-13: Sanitization for available locales and general clean up
* 2011-09-11: 1.0.2 release, still works appearantly
* 2010-01-05: Gem release
* 2009-03-12: Rails 2.3 compatible

---

Released under the MIT license
