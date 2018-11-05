### Octkit
---
https://github.com/octokit/octokit.rb

```
gem install octokit
gem "octokit", "~> 4.0"
require 'octkit'

script/bootstrap
script/console
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
