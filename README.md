# Hugo Web Monetization Component

**Note: This is not a standalone theme but a theme component that enables web monetization on all of your entire hugo website.**

[Web monetization](https://webmonetization.org/) is a standard. It is a JavaScript browser API which allows the creation of a payment stream from the reader to the content creator using the [Interledger Protocol](https://interledger.org/). The user needs a browser extension like [Coil](https://coil.com/) or [Minute](https://github.com/interledgerjs/minute), or they are ahead of their time and use the [Puma Browser](https://www.pumabrowser.com/). These will check the website for the existence of a `meta` tag called "monetization" which includes the [payment pointer](https://paymentpointers.org/).

This component adds a partial including the "monetization" `meta` tag and the payment pointer of the creator.

## How to add the component to your site

Add the component as second theme to your hugo site:
```
git submodule add git@github.com:sabinebertram/hugo-webmonetization-component.git themes/webmonetization
```

## How to configure and enable web monetization

In your `config.toml`, add the component to `theme`:
```toml
theme = ["YOUR-MAIN-THEME", "webmonetization"]
```

Additionally, add your [payment pointer](https://paymentpointers.org/) in the `params` section of your `config.toml`.
```toml
[params]
  monetization = "$twitter.xrptipbot.com/sabinebertram_"
```

The last part is a bit more tricky. You need to add the partial to the `head` of your website. Depending on how your main theme is set up, the location may be different. Here are two possibilities:

1. There is a `layouts/partials/head.html` or `layouts/partials/head/head.html`:

    Include the partial in the bottom of `head.html`:
    ```html
    {{ partial "webmonetization.html" .}}
    ```

2. The `head` is defined in `layouts/_default/baseof.html`

    Include the partial within the `head` tag:
    ```html
    <head>

      <!-- whatever else is there  -->

      {{ partial "webmonetization.html" .}}
    </head>
    ```

## TODO:
- [ ] Exclusive content
- [ ] Multiple payment pointers