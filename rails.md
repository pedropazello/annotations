# Rails Annotations

## Form
## Checkbox
`check_box_tag(:name, "value", <is checked or not (true|false)>,  { id: 'HTML id', class: 'HTML class' })`

## Working with arrays
brands as array in params

`check_box_tag('brands[]', 'Safety 1st', value, 'Safety 1st'), {})`

## Select from belongs to relation
`usp_image_form.collection_select :sku, @product.skus, :_id, :color, prompt: true`

## Multiple select
```
= filter_form.select(:tags,
   filter_form.object.tags.map {|tag| [tag, tag]}, { include_hidden: false }, { class: "select2", multiple: true })
```

## Nested Form
### Getting object array
https://stackoverflow.com/questions/18649027/how-to-get-the-index-of-children-in-a-nested-form

## Redirect Back
https://blog.bigbinary.com/2016/02/29/rails-5-improves-redirect_to_back-with-redirect-back.html

## Javascript
Rendering partial in js.erb file

`$('#comments ul.comments').append("<%= escape_javascript render(:partial => 'comments/single', :locals => { :c => @comment }) %>");`
