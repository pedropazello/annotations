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

## Asset pipeline
### Show all paths
`Rails.application.config.assets.paths`

## Controllers
### Actions as helpers
`helper_method :current_user, :logged_in?`

## Models
`validates :email, format: { with: URI::MailTo::EMAIL_REGEXP } `

## Reseting counter cache
https://yerb.net/blog/2014/03/13/three-easy-steps-to-using-counter-caches-in-rails/

## select2 ajax
https://www.prela.io/ajax-select2-with-rails

## generating random tokens
https://stackoverflow.com/a/12109098

