# get_shorty

A plugin for rails that shortens a url using the bitly shortening service and persists to the model.

* Default shortening provider is bitly
* Easily extendible by adding client / provider for other shortening service eg t.co from twitter when a public api is available.

## Installation

### As a rails plugin
  script/plugin install git://github.com/playgood/get_shorty.git
  
Then in the model that you want to add a short url to 

  Class ModelName
    include GetShorty
    has_short_url  
  end
    
has_short_url by default relies on the [Bitly](http://bit.ly/ "Bitly") API to shorten urls   
You need to register with Bitly to get a login and api_key. This needs to be set in a rails initializer to allow the Bitly provider to connect to your api account.

Or

You can roll out your own shortening provider - all it has to do is respond to the shorten method.
This can then be set using has_short_url option :shortening_service
For example:
  `Class ModelName
    include GetShorty
    
    has_short_url :shortening_service => MyShortener
  end`
  
_This assumes you have defined a Class `MyShortener` which respond to the method `shorten` with the parameter url_
## Note on Patches/Pull Requests
 
* Fork the project.
* Make your feature addition or bug fix.
* Add tests for it. This is important so I don't break it in a
  future version unintentionally.
* Commit, do not mess with rakefile, version, or history.
  (if you want to have your own version, that is fine but bump version in a commit by itself I can ignore when I pull)
* Send me a pull request. Bonus points for topic branches.

## TODO

* support for other ORM - at present only works with ActiveRecord
* support for other shortening url services.

## Copyright

Copyright (c) 2010 Louis Gillies. See LICENSE for details.