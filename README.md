[![Code Climate](https://codeclimate.com/github/gurix/helena.png)](https://codeclimate.com/github/gurix/helena) [![Build Status](https://travis-ci.org/gurix/helena.png?branch=master)](https://travis-ci.org/gurix/helena)
[![Coverage Status](https://coveralls.io/repos/gurix/helena/badge.png)](https://coveralls.io/r/gurix/helena)
[![Dependency Status](https://gemnasium.com/gurix/helena.png)](https://gemnasium.com/gurix/helena)

# Helena

## Installation
Add this line to your application's Gemfile:

    gem 'helena', git: 'git://github.com/gurix/helena.git'

And then execute:

    $ bundle install
    $ bundle exec rake helena:install:migrations
    $ bundle exec rake db:migrate
    
## Usage

Add this line to your routes will and you will be good to go!

    mount Helena::Engine => '/helena'

All helena controllers inherit from your `ApplicationController`. So define the `can_administer?` method in your `ApplicationController`. `can_administer?` determines whether current user can create/update survey questions.

Typical implementation would be:

```ruby
  class ApplicationController < ActionController::Base
    def current_user
      @current_user ||= User.find(session[:user_id])
    end

    def can_administer?
      current_user.try(:admin?)
    end
  end
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## Support

If you like helena and want to support the development, I would appreciate a donation:

[![Donate](https://www.paypalobjects.com/en_US/CH/i/btn/btn_donateCC_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=info%40markusgraf%2ech&lc=CH&item_name=Helena&currency_code=CHF&bn=PP%2dDonationsBF%3abtn_donateCC_LG%2egif%3aNonHosted)

## License

Helena is an online survey/test framework designed for agile
survey/test development, longitudinal studies and instant feedback.
Copyright (C) 2014  Markus Graf <info@markusgraf.ch>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
