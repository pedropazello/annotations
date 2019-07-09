# MongoDB

## Aggregation Framework
### Lookup with project

```
{
  from: 'catalog_products',
  as: 'product',
  'let': {
    product: '$_product'
  },
  pipeline: [
    {
      $project: {
        name: 1,
        _brand: 1,
        _categories: 1
      }
    },
    {
      $match: {
        $expr: {
          $eq: [
            '$$product',
            '$_id'
          ]
        }
      }
    }
  ]
}
```

### Check if Array field has one of the options of a array
```
{
  "product._categories": {
    $elemMatch:  { $in: ['5d24a33bfbc4efe6f104fce3'] } 
  }
}
```

### Searching by range
```
{
  $or: [
    { 
      price: {
        $gte: 1, $lte: 88.8
      }
    }
  ]
}
```

### Check if literal field have one of the items of a array
```
{
  $expr: {
    $in: [
      '$product._brand',
      ['Safety 1st', 'Quinny']
    ]
  }
}
```
