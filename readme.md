# wm-marketplace

This is a simple sdk to use when interacting with the [Walmart mMrketplace API][apiDocs]
Under a lot of work right now and is not safe to use in production. PR's welcome.

## Examples

Installation:
```js
npm i mws-marketplace -S

```

Initialization:
You will need your api credentials from walmart which can be gotten [here][credentials]
The walmart docs don't really say much on this, but your correlation id is any arbitrary string.
Channel type will appear beneath your consumer and private keys.

```js
const WMClient = require('wm-marketplace')
const wmc = WMClient({
  consumerId: 'your-consumer-id',
  privateKey: 'your-private-key',
  correlationId: 'your-correlation-id',
  channelType: 'your-channel-type'
})
```

Usage:

```js
wmc.Inventory.GetInventory({
  sku: 'your-sku'
})
.then((result) => {
  // API Response
})
```

## Roadmap
* Update the host to accept countries other than the US
* Finish adding all of the endpoints
* Add in throttling / pagification
* Add File upload


##Available Endpoints (updated as more are added)

### Orders
[Walmart Documentation][walmart-orders]

GetAll
[Walmart Documentation][walmart-orders-getall]

Available Parameters:
* sku: string
* customerOrderId: string
* purchaseOrderId: string
* status: string. Available Statuses: [Created, Acknowledged, Shipped, Canceled]
* createdStartDate: string. Available formats: [UTC date, timestamp]
* toExpectedShipDate: string. Format: YYYY-MM-DD
* limit: string. Restrictions: Less than 200

Usage:
```js
mws.Orders.GetAll({
  // Your parameters
})
```

### Inventory
[Walmart Documentation][walmart-inventory]

GetInventory
[Walmart Documentation][walmart-inventory-get]

Available Parameters:
* sku: string

Usage:
```js
mws.Inventory.GetInventory({
  // Your parameters
})
```

[apiDocs]: https://developer.walmart.com/#/apicenter/marketPlace/latest
[credentials]: https://seller.walmart.com/api-key

[walmart-orders]: https://developer.walmart.com/#/apicenter/marketPlace/latest#orderManagement
[walmart-orders-getall]: https://developer.walmart.com/#/apicenter/marketPlace/latest#getAllOrders

[walmart-inventory]: https://developer.walmart.com/#/apicenter/marketPlace/latest#inventoryManagement
[walmart-inventory-get]: https://developer.walmart.com/#/apicenter/marketPlace/latest#getInventoryForAnItem