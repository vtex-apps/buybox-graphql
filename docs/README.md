# Buybox GraphQL

[<i class="fa-brands fa-github"></i> Source code](https://github.com/vtex-apps/buybox-graphql)

> ⚠️ This app is no longer maintained by VTEX. This means support and maintenance are no longer provided.

This app exports a GraphQL schema to sort sellers on [buybox-context](https://github.com/vtex-apps/buybox-context).

### Installation

To use it in your app, add the following dependency in the `manifest.json` file:
```json
  "dependencies": {
    "vtex.buybox-graphql": "0.x"
  }
```

> This app is used on [buybox-context](https://github.com/vtex-apps/buybox-context), but you may then use it in your front-end component as well.

To resolve this query, you must have an app installed in your workspace that implements the GraphQL interface. Currently, those are the available resolvers:

- [buybox-resolver](https://github.com/vtex-apps/buybox-resolver)

> Having zero or more than one resolver installed will result in an error.

### Examples

Using this resolver, you can provide information about the `Product` and `Shipping` to get an array of sorted sellers. The returned array is a list of `sellerId` values.

```graphql
query SortSellersProtocol {
  sortSellers(skuId: "33", postalCode: "00000000", country: "BRA", salesChannel: 1) {
    sellers
  }
}
```

This returns sellers' IDs inside the `Product`. Here's a possible response for the execution of this query:

```graphql
{
  "data": {
    "sortSellers": {
      sellers: ["seller1", "seller3", "seller4", "otherSeller"]
    }
  }
}
```
