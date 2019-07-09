# MongoDB

## Aggregation Framework
### $lookup with project

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

### $match if Array field has one of the options of a array
```
{
  "product._categories": {
    $elemMatch:  { $in: ['5d24a33bfbc4efe6f104fce3'] } 
  }
}
```

### $match by range
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

### $match literal field have one of the items of a array
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
