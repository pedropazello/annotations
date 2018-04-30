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
