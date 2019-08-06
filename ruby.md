# Ruby annotations
## How to create .ruby-version and .ruby-gemset
`rvm --create --ruby-version ruby-1.9.3@my-gemset`

## .editorconfig for Ruby apps
```
root = true

[*]
indent_style = space
indent_size = 2
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[*.{sh,markdown}]
indent_size = 4

```

## Different Ways to Set Attributes in ActiveRecord

[http://www.davidverhasselt.com/set-attributes-in-activerecord](http://www.davidverhasselt.com/set-attributes-in-activerecord/)

## Short lambda Syntax from Ruby 1.9
```
twice = -> (x) { 2 * x }
twice.call(5) # => 10
```

## Remove file from carrierwave
```
# Object is the activeRecord object and remove_*uploader* is the name of column used by uploader
object.update(remove_uploader: true)
```

## jquery-ujs events list

[https://github.com/rails/jquery-ujs/wiki/ajax#custom-events-fired-during-data-remote-requests](https://github.com/rails/jquery-ujs/wiki/ajax#custom-events-fired-during-data-remote-requests)

## Carrierwave: Validate filesize
[https://github.com/carrierwaveuploader/carrierwave/wiki/How-to%3A-Validate-image-file-size](https://github.com/carrierwaveuploader/carrierwave/wiki/How-to%3A-Validate-image-file-size)

## Increase/disable timeout time on activerecord-safer_migrations gem
```
class LockTest < ActiveRecord::Migration
  set_lock_timeout(250)
  set_statement_timeout(750)

  def change
    create_table :lock_test
  end
end

To disable timeouts use disable_lock_timeout! and disable_statement_timeout!
```
## Sidekiq testing options
[https://github.com/mperham/sidekiq/wiki/Testing#setup](https://github.com/mperham/sidekiq/wiki/Testing#setup)

## Check if Array have specific item
`array.include?(item)`

## Capistrano
When capistrano ask for password when deploy command is running

[https://stackoverflow.com/questions/3269578/capistrano-asks-for-password-when-deploying-despite-ssh-keys](https://stackoverflow.com/questions/3269578/capistrano-asks-for-password-when-deploying-despite-ssh-keys)

## Clockwork gem
Procfile (if using Dokku)
```
web: bundle exec puma -C config/puma.rb
worker: bundle exec sidekiq -c 5 -v
schedule: clockwork clock.rb
```

clock.rb
```
require 'clockwork'
require 'active_support/time'
require './config/boot'
require './config/environment'

module Clockwork
  handler do |job|
    puts "Running #{job}"
  end

  every(5.minute, 'invoices_mailers.send') do
    `rake invoices_mailers:send`
  end
end
```

## Upcase and Downcase
```
"hello James!".upcase      #=> "HELLO JAMES!"
"hello James!".capitalize  #=> "Hello james!"
"hello James!".titleize    #=> "Hello James!"
string.downcase!           #=> "hello james!"
```

## Wicked PDF
### Mac OSX low resolution problem
in `config/initializers/wicked_pdf.rb`

```
if Rails.env.development?
  WickedPdf.config[:lowquality] = true
  # WickedPdf.config[:exe_path] = '/usr/local/bin/wkhtmltopdf'
end
```
### Render PDF
```
render pdf: "print_externo", show_as_html: params[:as_html]
```
### Template
```
<!DOCTYPE html>
<meta charset="utf-8"/>
<html>
  <head>
    <title>PDF</title>
    <%#= stylesheet_link_tag 'application', media: 'all' %>
    <%= wicked_pdf_stylesheet_link_tag "https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" %>
    <style>
    </style>
  </head>
  <body>
  </body>
</html>

```

## I18n
### Attribute translation
`t('activerecord.attributes.model.attribute')`

## Find rows with multiple duplicate fields with Active Record, Rails & Postgres
[https://stackoverflow.com/questions/21669202/find-rows-with-multiple-duplicate-fields-with-active-record-rails-postgres](https://stackoverflow.com/questions/21669202/find-rows-with-multiple-duplicate-fields-with-active-record-rails-postgres)
