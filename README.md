## int, asynchronous continuous integration

int is a simple way to ensure your code is always on sync, fully tested
and has full test coverage. All without a different CI machine. This is
meant to run right from the developer's machine.

## Requirements

* OSX is currently supported. Linux might work, but it's not throughly
  tested.

* [heroku-toolbelt](https://toolbelt.heroku.com/). You can either
install it with `brew install heroku-toolbelt` or use the package
provided for your OS.

* RSpec for testing.

* We use simplecov for code coverage.

## Getting Started

Install using brew and follow the instructions that follow.

```
brew install https://raw.github.com/Helabs/int/stable/int.rb --HEAD
```

## Usage

* Add your Heroku app to `.rvmrc` using the environment variable `APP`:

```
APP=my_heroku_app
```

* If you always want 100% code coverage, add this on
   top of your spec/spec_helper.rb:

```ruby
if ENV['COVERAGE'] == 'on'
  require 'simplecov'
  SimpleCov.start 'rails' do
    minimum_coverage 100
    add_filter "app/admin/"
  end
end
```

int already sets `COVERAGE` to on when running int spec.

* Finally, integrate your code!

```
int run
```

You can checkout the list of tasks on the [int-run](libexec/int-run) command.

## Features/Problems

* We only support OSX;
* We only support RSpec;
* We only support Rails.
* Upgrade currently only works by doing `brew rm int` and reinstalling.
  There is an issue opened at [homebrew](https://github.com/mxcl/homebrew/issues/13197).

## License

int is released under the [MIT License](http://www.opensource.org/licenses/MIT).