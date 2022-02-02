# shurjoPay2 integration for nodejs sites

## Checkout, Verify

- Generate token for merchants
- perform checkout
- Check order status
- Verify order id

## Requirement
- nodejs >=13.0

## Install

```shell
# npm versions > 5
npm i shurjopay
```

## Docs/Usage

__Example integration use case scenario is expressCart(https://github.com/mrvautin/expressCart)__

Loading the module gets us a factory function, calling it instantiates the module.

```javascript
const sp_factory = require('shurjopay');
const shurjopay = sp_factory();
// now set environment to live
shurjopay.is_live();

//  The minimum config/environment variables that your site need to maintain(config related to shurjopay)
const spConfig = {
    "client_id": "your merchant id",
    "client_secret": "your merchant password or secret token",
    "client_key_prefix": "sp",
    "currency": "BDT"
}
// Now call the object configure method
shurjopay.configure_merchant(spConfig.client_id, spConfig.client_secret, spConfig.client_key_prefix, spConfig.currency);

// Now proceed with the rest of your route and controller logic. 
```

The object provides methods that you need to use are:

- Payment operation methods: `checkout`, `verify`, `check_status`, `token_valid`.
- Configuration methods: `configure_merchant`
- Error handler methods: `gettoken_error_handler`, `checkout_error_handler`
- Callback handler methods: `checkout_callback`
- Module's own settings object: `sp.settings`
- Store session accessor: `sp.session`

#### In your route controllers, your workflow is (using three routes):

- At checkout->payment method, selecting shurjopay lands the buyer in _checkout_action_ route, where you initiate the transaction with cart details
- At first configure the shurjopay object to set the merchant info
- Then set the checkout_return and checkout_cancel callback url
- Then set the session accessor
- Then set error handlers, checkout callback
- Then call the checkout method

### An example route controller is already written for you (expressjs-mongodb)

Check over the /examples folder.

#### Some sample api response formats

check the /docs folder.

<!--
## Contact

Minhajul Anwar; [resgef.com][resgef-url], Dhaka, Bangladesh.
<br>**Email:** [contact@resgef.com](mailto:contact@resgef.com)

## Questions or need help?

Come talk to us on the [GitHub discussion][gh-discussion]

## Social Media and links

[Twitter](https://twitter.com/intent/follow?original_referer=https%3A%2F%2Fgithub.com%2FMinhajulAnwar&screen_name=MinhajulAnwar) &nbsp;&nbsp;
[GitHub-Blog](https://minhajme.github.io/blog/) &nbsp;&nbsp;
-->
<br>[https://resgef.com][resgef-url] &nbsp;&nbsp;

[ff-introsite-gh-pages]: https://freightforward.github.io

[ff-doc-gh-pages]: https://freightforward.github.io/docs/

[gh-discussion]: https://github.com/minhajme/sp2nodejs/discussions

[dev-gh]: https://github.com/minhajme

[resgef-url]: https://resgef.com
