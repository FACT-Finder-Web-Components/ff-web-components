FACT-Finder Web Components
==========================
Predictive Basket branch (experimental)
---------------------------------------

This branch introduces the `ff-predictive-basket` element for easy integration with the new FACT-Finder Predictive Basket feature. To use it, you need FACT-Finder version **7.3** or higher.

_Note that this feature is at an experimental stage and changes may occur._

### The Predictive Basket Element

The following listing shows the newly introduced element. The element itself does not have a visual component and must be used in combination with an `ff-record-list` in the same manner as `ff-recommendation`. See further below for more details.

```html
<ff-predictive-basket user-id="123456"
                      max-results="10"
                      certainty="60"
                      blacklist="art-id1,art-id2">
    <!-- requires ff-record-list here to work -->
</ff-predictive-basket>
```

Once the element is correctly initialized, it will automatically issue a request to FACT-Finder and display the result. This will happen only once per page load. If you need to refresh the displayed data, refer to the `getPredictions()` method below.

#### Attributes

Attribute | Required | Type | Default | JS property
--------- | -------- | ---- | ------- | -----------
user-id   | yes      | String | _(none)_ | `userId`

The ID of the user for whom products shall be predicted. If the user ID is not specified, no request to FACT-Finder will be issued.



Attribute | Required | Type | Default | JS property
--------- | -------- | ---- | ------- | -----------
max-results | optional | Number |  _(unlimited)_ | `maxResults`

The maximum amount of products to be returned from FACT-Finder. To receive all predictions, omit this attribute or set its value to `-1`.


Attribute | Required | Type | Default | JS property
--------- | -------- | ---- | ------- | -----------
certainty | optional | Number | 60    | `certainty`

This value is the minimum percentage to which the prediction algorithm is certain that the user will buy the product. Products with a lower certainty will not be returned from FACT-Finder.


Attribute | Required | Type | Default | JS property
--------- | -------- | ---- | ------- | -----------
blacklist | optional | String (comma-separated list) | _(empty)_ | `blacklist`

With the `blacklist` attribute you can specify one or more product IDs that shall not be returned from FACT-Finder. This may be useful if you, for example, don't want products to appear in the predictions once the user has placed them in their shopping cart.

#### Methods

##### `predictiveBasketElement.getPredictions()`

This method issues a request to FACT-Finder with the currently set values.


### Example Setup

#### HTML
```html
<ff-predictive-basket user-id="123456" max-results="10" certainty="80" blacklist="art-id1,art-id2">
    <ff-record-list subscribe="false">
        <ff-record>
            <img data-image="{{record.image}}" data-image-onerror="../img_not_found.gif">
            <div>
                <a data-anchor="{{record.deeplink}}" data-redirect="{{record.deeplink}}">
                    {{record.name}}
                </a>
                <div>Price: <strong>{{record.price}}</strong></div>
            </div>
        </ff-record>
    </ff-record-list>
</ff-predictive-basket>
```

#### Manual update with `blacklist`
```js
function onUpdate(itemsToExclude) {
    const predBasket = document.querySelector("ff-predictive-basket");
    predBasket.blacklist = itemsToExclude;  // itemsToExclude must be a comma-separated list
    predBasket.getPredictions();
}
```


## General Notes

This distribution provides only the build including all dependencies (Polymer 3, Lit Element). If you need to use/include each element separately, please refer to your FACT-Finder Project Developer.

See [web-components.fact-finder.de](http://web-components.fact-finder.de/) for the complete documentation including Get Started, Developer Guide and more.



## Installation

Directly from GitHub via npm.

For latest update:
```
npm i git+https://git@github.com/FACT-Finder-Web-Components/ff-web-components.git#release/BETA-predictive-basket
```

Specific version via commit ID:
```
npm i git+https://git@github.com/FACT-Finder-Web-Components/ff-web-components.git#fdfb064
```

Or via package.json:
```json
"dependencies": {
  "ff-web-components": "git+https://git@github.com/FACT-Finder-Web-Components/ff-web-components.git#release/BETA-predictive-basket"
}
```
