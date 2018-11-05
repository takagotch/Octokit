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
