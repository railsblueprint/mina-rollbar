# Mina::Rollbar 
[Mina](https://github.com/mina-deploy/mina) tasks for interacting with [Rollbar](http://rollbar.com).

This is updated version of [Mina::Rollbar](https://github.com/code-lever/mina-rollbar). 
Supports separate deployment started/finished notifications in rollbar.

Adds the following tasks:

    rollbar:notify:starting
    rollbar:notify:finished

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'mina-rollbar-3', require: false
```

And then execute:

    $ bundle

## Usage

    require 'mina/rollbar'

    ...
    # replace value w/your real access token
    set :rollbar_access_token, 'this-is-not-a-real-token'

    task deploy: :environment do
      run(:local) do
        invoke :'rollbar:starting'
      end

      deploy do
        ...

        on :launch do
          ...
        end
      end

      run(:local) do
        invoke :'rollbar:finished'
      end
    end

## Options

| Name                         | Description                                            |
| ---------------------------- | ------------------------------------------------------ |
| `rollbar_access_token`       | Rollbar access token (post_server_item token)          |
| `rollbar_username`           | Rollbar username of deploying user (optional)          |
| `rollbar_local_username`     | Local username of deploying user (optional)            |
| `rollbar_comment`            | Comment for this deployment (optional)                 |
| `rollbar_env`                | Deployment environment string, defaults to `rails_env` |

## Contributing

1. Fork it ( https://github.com/railsblueprint/mina-rollbar/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
