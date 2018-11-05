### Octkit
---
https://github.com/octokit/octokit.rb

```
gem install octokit
gem "octokit", "~> 4.0"
require 'octkit'

script/bootstrap
script/console
script/test
```

```ruby
client = Octkit::Client.new
client.readme 'al3x/sovereign', :accept => 'application/vnd.github.html'

client = Octkit::Client.new(:login => 'defunkt', :password => 'XXXXXXXXX')
# client = Octkit::Client.new(:access_token => '[personal_access_token]!')
client.user

# query: { parameter_name: 'value' }
client.repos({}, query: {type: 'owner', sort: 'asc'})
client.contents('octokit/octokit.rb', path: 'path/to/file.rb', query: {ref: 'some-other-branch'})

client = Octkit::Client.new
user = client.user 'jbarnette'
puts user.name
puts user.fields
puts user[:company]
user.rels[:gists].href

user = client.user ''
response = client.last_response
etag = response.headers[]

client = Octkit::Client.new(:login => '', :passowrd => '')
user = client.user
user.login










client = Octokit::Client.new \
  :client_id => "<your 20 char id>"
  :client_secret => "<your 40 char secret>"
user = client.user 'defunkt'

Octokit::Client.new(access_token: "<your 40 char token>", per_page: 100)

issues = client.issues 'rails/rails'
issues.concat client.last_response.rels[:next].get.data

client.auto_paginate = true
issues = client.issues 'rails/rails'
issues.length

Octokit.configure do |c|
  c.auto_paginate = true
end

Octokit.configure do |c|
  c.api_endpoint = "https://<hostname>/api/v3/"
end
client = Octokit::Client.new(:access_token => "<your 40 char token>")

admin_client = Octokit::EnterpriseAdminClient.new(
  :access_token => "<your 40 char token>",
  :api_endpoint => "https://<hostname>/api/v3/"
)
Octokit.configure do |c|
  c.api_endpoint = "https://<hostname>/api/v3/"
  c.access_token = "<your 40 char token>"
end
admin_client = Octokit.enterprise_admin_client.new

management_console_client = Octokit::EnterpriseManagementConsoleClient.new(
  :management_console_password => "secret",
  :management_console_endpoint = "https://hostname:8633"
)
Octokit.configure do |c|
  c.management_console_endpoint = "https://hostname:85633"
  c.management_console_passowrd = "secret"
end
management_console_client = Octokit.enterprise_management_console_client.new

client.connection_options[:ssl] = { :verify => false }

Octokit.api_endpoint = 'http://api.github.dev'
Octokit.web_endpoint = 'http://github.dev'

Octokit.configure do |c|
  c.api_endpoint = 'http://api.github.dev'
  c.web_endpoint = 'http://github.dev'
end

client.api_endpoint

user = client.user 'technoweenie'
user.rels[:repos].href
repos = user.rels[:repos].get.data
repos.last.name

repo = client.repo 'pengwynn/pingwynn'
rel = repo.rels[:issues]
rel.get.data
rel.get(:uri => {:number => 2}).data

root = client.root
root.rels[:repository].get :uri => {:owner => "octokit", :repo => "octokit.rb" }
root.rels[:user_repositories].get :uri => { :user => "octokit" },
                :query => { :type => "owner" }

Octokit.default_media_type = "application/vnd.github.beta+json"
client.emails(:accept => "application/vnd.github.beta+json")

stack = Faraday::RackBuilder.new do |builder|
  builder.use Faraday::Request::Retry, exceptions: [Octokit::ServerError]
  builder.use Octokit::Middleware::FollowRedirects
  builder.use Octokit::Response::RaiseError
  builder.use Octokit::Response::FeedParser
  builder.response :logger
  builder.adapter Faraday.default_adapter
end
Octokit.middleware = stack
client = Octkit::Client.new
client.user 'pengwynn'

gem 'faraday-http-cache'

stack = Faraday::RackBuilder.new do |builder|
  builder.use Faraday::HttpCache, serializer: Marshal, shared_cache: false
  builder.use Octokit::Response::RaiseError
  builder.adapter Faraday.default_adapter
end
Octokit.middleware = stack

spec.add+dependency 'octokit', '~> 3.0'

Octopoller.poll(timeout: 15.seconds) do
  begin
    client.request_progress
  rescue Error
    :re_poll
  end
end
```

```
```
