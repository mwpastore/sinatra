# Why use bundler?
# Well, not all development dependencies install on all rubies. Moreover, `gem
# install sinatra --development` doesn't work, as it will also try to install
# development dependencies of our dependencies, and those are not conflict free.
# So, here we are, `bundle install`.
#
# If you have issues with a gem: `bundle install --without-coffee-script`.

RUBY_ENGINE = 'ruby' unless defined?(RUBY_ENGINE)
source 'https://rubygems.org' unless ENV['QUICK']
gemspec

gem 'rack-test', '>= 0.6.2'
gem 'minitest', '~> 5.0'

# Allows stuff like `tilt=1.2.2 bundle install` or `tilt=master ...`.
# Used by the CI.
{
  'tilt' => 'rtomayko/tilt',
  'rack' => 'rack/rack'
}.each do |lib, req|
  dep = case (env = ENV[lib])
        when 'stable', nil then nil
        when /(?:\d+\.)+\d+/ then '~> ' + env.sub("#{lib}-", '')
        else {:github => req, :branch => env}
        end
  gem lib, dep
end

if Gem::Version.new(RUBY_VERSION.dup) < Gem::Version.new('1.9')
  gem 'json', '< 2'
end

if Gem::Version.new(RUBY_VERSION.dup) >= Gem::Version.new('1.9.3')
  gem 'RedCloth'
  gem 'asciidoctor'
  gem 'bluecloth'
  gem 'builder'
  gem 'coffee-script', '>= 2.0'
  gem 'creole'
  gem 'erubis'
  gem 'haml', '>= 3.0'
  gem 'i18n'
  gem 'kramdown'
  gem 'less', '~> 2.0'
  gem 'markaby'
  gem 'maruku'
  gem 'net-http-server'
  gem 'puma'
  gem 'rabl'
  gem 'radius'
  gem 'rake'
  gem 'rdiscount'
  gem 'rdoc'
  gem 'redcarpet'
  gem 'sass'
  gem 'slim', '~> 2.0'
  gem 'stylus'
  gem 'therubyracer'
  gem 'thin'
  gem 'wikicloth'
  gem 'wlang', '>= 2.0.1'
  gem 'yajl-ruby'
else
  gem 'i18n', '< 0.7'
  gem 'mini_portile2', '< 2.0'
  gem 'rake', '< 11'
end

if Gem::Version.new(RUBY_VERSION.dup) >= Gem::Version.new('2.1.0')
  gem 'liquid'
  gem 'nokogiri'
else
  gem 'liquid', '< 4'
  gem 'nokogiri', '< 1.7'
end

if Gem::Version.new(RUBY_VERSION.dup) >= Gem::Version.new('2.2.2')
  gem 'activesupport'
elsif Gem::Version.new(RUBY_VERSION.dup) >= Gem::Version.new('1.9.3')
  gem 'activesupport', '< 5'
else
  gem 'activesupport', '< 4'
end

case RUBY_ENGINE
when 'jruby'
  gem 'jruby-openssl'
  gem 'trinidad'
when 'rbx'
  gem 'json'
  gem 'rubysl'
  gem 'rubysl-test-unit'
end
