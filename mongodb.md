# MongoDB

## running as daemon

https://coderwall.com/p/bf1iqg/run-mongodb-as-a-daemon

## dump/restore
`mongodump --db=pricepoint3_production --collection=where_to_buy --out=data_where_to_buy`

`mongorestore --db sistrading5_stage --collection service_digital_where_to_buys data_where_to_buy/pricepoint3_production/where_to_buy.bson --drop`

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

### Match with and
```
{
  $and: [
    { "filters.name": { $eq: "colors" } },
    { "filters.tags": { $in: ['black'] } }
  ]
}
```
### Converting object type in aggregation
```
 {
        '$lookup': {
            'from': 'catalog_sales_prices', 
            'as': 'sales_prices', 
            'let': {
                'skuId': '$_id'
            }, 
            'pipeline': [
                {
                    '$project': {
                        'value': 1, 
                        '_sku': 1, 
                        'table': 1
                    }
                }, {
                    '$replaceRoot': {
                        'newRoot': {
                            '$mergeObjects': [
                                '$$ROOT', {
                                    'value': {
                                        '$toDecimal': '$value'
                                    }
                                }
                            ]
                        }
                    }
                }, {
                    '$match': {
                        '$expr': {
                            '$eq': [
                                '$$skuId', '$_sku'
                            ]
                        }
                    }
                }
            ]
        }
    }
```

## Lookup with $arrayElemAt
```
/**
 * specifications - The fields to
 *   include or exclude.
 */
{
  _channel: 1,
  _sku: 1,
  uri: 1,
  sku: { $arrayElemAt: ["$sku", 0] }
}
```
