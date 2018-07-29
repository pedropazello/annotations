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
