# Jquery Annotations

## Getting Values from data
To get value from `data-name`

`$("#something").data("name")`

## Converting number field to R$ format
```
  $(".monetary-value").each(function(index) {
    var value = $(this).val()
    var valueAsFloat = parseFloat(value)

    if (!isNaN(valueAsFloat)) {
      var valueFormatted = valueAsFloat.toFixed(2).replace(".", ",")
      console.log(valueFormatted)
      $(this).val(valueFormatted)
    }
  })
```
