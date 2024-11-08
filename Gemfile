source 'https://rubygems.org'

gemspec

git 'https://github.com/refinery/refinerycms', '-> 3.0.2' do
  gem 'refinerycms'

  group :development, :test do
    gem 'refinerycms-testing'
  end
end

group :test do
  gem 'launchy'
  gem 'pry'
  gem 'poltergeist'
  gem 'listen'
end

# Database Configuration
unless ENV['TRAVIS']
  gem 'activerecord-jdbcsqlite3-adapter', '>= 1.3.0.rc1', platform: :jruby
  gem 'sqlite3', platform: :ruby
end

if !ENV['TRAVIS'] || ENV['DB'] == 'mysql'
  group :mysql do
    gem 'activerecord-jdbcmysql-adapter', '>= 1.3.0.rc1', :platform => :jruby
    gem 'mysql2', :platform => :ruby
  end
end


if !ENV['TRAVIS'] || ENV['DB'] == 'postgresql'
  group :postgres, :postgresql do
    gem 'activerecord-jdbcpostgresql-adapter', '>= 1.3.0.rc1', :platform => :jruby
    gem 'pg', :platform => :ruby
  end
end

# Refinery/rails should pull in the proper versions of these
group :assets do
  gem 'sass-rails'
  gem 'coffee-rails'
end

# Load local gems according to Refinery developer preference.
if File.exist? local_gemfile = File.expand_path('../.gemfile', __FILE__)
  eval File.read(local_gemfile)
end
