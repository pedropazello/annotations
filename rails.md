# Rails Annotations

## Form
## Checkbox
`check_box_tag(:name, "value", <is checked or not (true|false)>,  { id: 'HTML id', class: 'HTML class' })`

## Working with arrays
brands as array in params

`check_box_tag('brands[]', 'Safety 1st', value, 'Safety 1st'), {})`

## Javascript
Rendering partial in js.erb file

`$('#comments ul.comments').append("<%= escape_javascript render(:partial => 'comments/single', :locals => { :c => @comment }) %>");`
