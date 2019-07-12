# Rails Annotations

## Form
## Checkbox
`check_box_tag(:name, "value", <is checked or not (true|false)>,  { id: 'HTML id', class: 'HTML class' })`

## Working with arrays
brands as array in params

`check_box_tag('brands[]', 'Safety 1st', value, 'Safety 1st'), {})`

## Select from belongs to relation
`usp_image_form.collection_select :sku, @product.skus, :_id, :color, prompt: true`

## Javascript
Rendering partial in js.erb file

`$('#comments ul.comments').append("<%= escape_javascript render(:partial => 'comments/single', :locals => { :c => @comment }) %>");`
