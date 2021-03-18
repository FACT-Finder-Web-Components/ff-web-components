# 4.0.1
## FIX
- `ff-suggest-item`
  - item's title gets overwritten with HTML for hit highlighting
  - clicking product suggestion does not redirect to PDP with API v4
- `core`
  - price is localized twice if field with role `price` is set in `currency-fields`
- `ff-communication`
  - `add-params` overwrites manually selected filters


# 4.0.0
## BREAKING
- `ff-communication`
  - `version` default value removed. `version` must now always be specified
  - `api` default value removed. `api` must now always be specified when `version="ng"`
  - removed attributes `disable-single-hit-redirect` and `single-hit-redirect-base-path`
- `ff-searchbox`
  - removed `hidesuggest-onblur` attribute
- `ff-record-list`, `ff-record`
  - removed `stamp-always` attribute
- `ff-asn`
  - `for-group` attribute references `associatedFieldName` now
- `ff-slider`
  - no longer emits `search` events
- `ff-breadcrumb-trail-item`, `ff-single-word-search-record`
  - removed `clone` method
- `ff-checkout-tracking`
  - remove `records` property
- `core`
  - removed _Single Hit Redirect_ feature
  - removed `factfinder.communication.FFCommunicationEventAggregator`
  - prices in `getRecords` response are localized now

## ADD
- FACT-Finder NG API **v4** support
  - activate it through the `ff-communication` element
    ```html
    <ff-communication version="ng" api="v4"></ff-communication>
    ```
  - Customer Specific Pricing (CSP) through new `purchaser-id` attribute on `ff-communication`
    ```html
    <ff-communication version="ng" api="v4" purchaser-id="123456"></ff-communication>
    ```
  - `ff-campaign-product` got new attribute `id-type`. It can be set to either `productNumber` or `id`
    ```html
    <ff-campaign-product record-id="1234" id-type="productNumber"></ff-campaign-product>
    ```
- `ff-campaign-pushed-products`, `ff-campaign-feedbacktext`
  - introduced new attribute `is-landing-page-campaign` which can be used in combination with the `ff-campaign-landing-page` element
- Tracking
  - introduced new form of tracking: `LandingPageClick`

## FIX
- `ff-communication`
  - `navigation="true"` in `add-params` doesn't send a navigation request
  - element sends an invalid search request when a whitespace or empty string is set to the attribute `default-query` and `search-immediate` is in use
- `ff-searchbox`
  - element renders `undefined` if `ff-communication` attribute `default-query` is set to empty string or set without any value
- `ff-suggest`
  - suggest types containing whitespace are not supported
- `ff-asn-group`
  - element sends redundant category filters in NG when resetting filter
- `ff-recommendation`
  - click tracking sends invalid request
- `ff-similar-products`
  - attribute `max-results` does not work in NG
  - element got new attribute `id-type`. It can be set to either `productNumber` or `id`. This attribute is mandatory when using FACT-Finder NG
    ```html
    <ff-similar-products record-id="1234" id-type="productNumber"></ff-similar-products>
    ```
- `ff-navigation`, `ff-header-navigation`
  - elements do not render nested elements
- `ff-sortbox`
  - prevent templates from being parsed more than once
- `ff-products-per-page-dropdown`, `ff-products-per-page-list`, `ff-products-per-page-select`
  - element does not remove `page` parameter when one of its items is selected
- request types `productDetail` and `getRecords` now emit cancellable `before-*` events (`before-productDetail`, `before-getRecords`); previously a generic `before-search` event was emitted
  - cancellable through `preventDefault()`
- `ff-checkout-tracking`
  - element sends `query` in the tracking request
  - element sends `null` as a price
- Tracking
  - click tracking does not send correct query using NG
  - click tracking throws an error when category filter is missing using FACT-Finder NG
  - cart tracking sends an invalid request when a custom price field name is used and localization is enabled
- `core`
  - doesn't emit an error when `sid` is not exactly 30 characters length
  - campaign requests don't consider `purchaserId`
  - `navigation` event's `endLevel` defaults to `"null"`

## IMPROVE
- `ff-slider-one-touch`
  - `touchstart` listeners are now passive

## DEPRECATION
_Usage of these features is no longer recommended. They are going to be **removed** in a future version._
- `new factfinder.communication.Tracking12()` and `factfinder.communication.trackingManager`
  - replaced by static namespace `factfinder.communication.Tracking`
  - instantiation is no longer required


# 4.0.0-rc.3
## BREAKING
- `ff-communication`
    - `version` default value removed. `version` must now always be specified
    - `api` default value removed. `api` must now always be specified when `version="ng"`

## ADD
- `ff-campaign-pushed-products`
    - introduced new attribute `is-landing-page` which can be used in combination with `ff-campaign-landing-page` element
- `tracking`
    - introduced new form of tracking: `LandingPageClick`

## FIX
- `ff-similar-products`
    - element got new attribute `id-type`. It can be set to either `productNumber` or `id`. This attribute is mandatory when using FACT-Finder NG
      ```html
      <ff-similar-products record-id="1234" id-type="productNumber"></ff-similar-products>
      ```
- `ff-navigation`, `ff-header-navigation`
    - elements do not render nested elements
- tracking
    - click tracking does not send correct query using NG
- `ff-asn-group`
    - element sends redundant category filters in NG when resetting filter
- `ff-sortbox`
    - prevent templates from being parsed more than once
- `productDetail` and `getRecords` now emit cancellable `before-*` events (`before-productDetail`, `before-getRecords`); previously a generic `before-search` event was emitted
    - cancellable through `preventDefault()`


# 4.0.0-rc.2
## ADD
- FACT-Finder NG API v4 support
    - activate it through the `ff-communication` element
      ```html
      <ff-communication version="ng" api="v4"></ff-communication>
      ```
    - Customer Specific Pricing (CSP) through new `purchaser-id` attribute on `ff-communication`
      ```html
      <ff-communication version="ng" api="v4" purchaser-id="123456"></ff-communication>
      ```
    - `ff-campaign-product` got new attribute `id-type`. It can be set to either `productNumber` or `id`
      ```html
      <ff-campaign-product record-id="1234" id-type="productNumber"></ff-campaign-product>
      ```

## FIX
- `ff-checkout-tracking`
    - element sends `query` in the tracking request
    - element sends `null` as a price
- `core`
    - `navigation` event's `endLevel` defaults to `"null"`

## IMPROVE
- `ff-slider-one-touch`
    - `touchstart` listeners are now passive


# 4.0.0-rc.1
## BREAKING
- `ff-asn`
    - `for-group` attribute references associatedFieldName now
- `ff-communication`
    - removed attributes `disable-single-hit-redirect` and `single-hit-redirect-base-path`
- `core`
    - removed Single Hit Redirect feature
    - removed `factfinder.communication.FFCommunicationEventAggregator`
- `ff-searchbox`
    - removed `hidesuggest-onblur` attribute
- `ff-record-list`, `ff-record`
    - removed `stamp-always` attribute
- `ff-checkout-tracking`
    - remove `records` property
- `ff-slider`
    - no longer emits `search` events
- `breadcrumb-trail-item`, `single-word-search-record`
    - removed `clone` method
- increment default FACT-Finder version from `7.2` to `7.3`

## DEPRECATION
_Usage of these features is no longer recommended. They are going to be **removed** in a future version._
- `new factfinder.communication.Tracking12()` and `factfinder.communication.trackingManager`
    - replaced by static namespace `factfinder.communication.Tracking`
    - instantiation is no longer required


# 3.15.8
## FIX
- `ff-similar-products`
    - multiple instances subscribe to the same topic
- `ff-asn-group`, `ff-asn-group-slider`, `ff-sortbox`, `ff-paging-dropdown`, `ff-products-per-page-dropdown`
    - element does not expand when a CSS rule keeps part of the container visible
- `core`
    - `globalCommunicationParameter` takes incorrect default values when used without `ff-communication`


# 3.15.7
## IMPROVEMENT
- `core` / SSR
    - introduced `ResultDispatcher.dispatchRaw(response, topics)` function for manually dispatching responses as they are received from FACT-Finder (to be used in e.g. SSR)

## DEPRECATE
_Usage of these features is no longer recommended. They are going to be **removed** in a future version._
- `ff-communication.useUrlParameter`
    - renamed to `useUrlParameters`, corresponding attribute `use-url-parameter` renamed to `use-url-parameters` accordingly
- `core.globalCommunicationParameter.useUrlParameter`
    - renamed to `useUrlParameters`


# 3.15.6
## FIX
- `ff-breadcrumb-trail-item`, `ff-navigation`, `ff-filter-cloud`, `ff-suggest-item`
    - element does not decode text
- `ff-slider-one-touch`
    - `absoluteMinValue` and `absoluteMaxValue` round to incorrect integers
- `ff-slider`
    - slider sends request with duplicated parameters with wrong encoding
- `ff-predictive-basket` _(experimental feature - not yet stable and subject to change)_
    - returned records have incorrectly formatted prices


# 3.15.5
## FIX
- `ff-suggest-item`
    - element ignores `deeplink` from the suggest response causing redundant requests to the Records API

## IMPROVE 
- `ff-slider-one-touch`
    - min/max markers are now draggable
    - added purely visual `div.ffw-selected-range` element that spans in the selected range on the slider rail

## EXPERIMENTAL
_Experimental features are not yet stable and subject to change._
- `ff-predictive-basket`
    - introduced new element
    - activate through setting `factfinder.__experimental.predictiveBasket.enable = true`


# 3.15.4
## FIX
- `ff-header-navigation`
    - element's body doesn't open when hovering over navigation item


# 3.15.3
## FIX
 - `core`
    - `associatedFieldName` is populated with incorrect values in NG environment
    - `+` signs in query parameters are no longer converted to `%20` after refreshing the page
- `ff-asn-group-element`
    - element sends duplicate requests
- `ff-filter-cloud`
    - element displays implicit filters
- `ff-slider`
    - emits `search` event unlike other ASN groups which emit `filter`
    - now emits additional event of type `filter` on submit  
      NOTE: `search` event is deprecated and should no longer be relied on

## DEPRECATE
_Usage of these features is no longer recommended. They are going to be **removed** in a future version._
- `ff-slider` - `search` event
    - emitting a `search` event after selecting a value is inconsistent with the rest of filters which emit `filter` events


# 3.15.2
## FIX
- `ff-asn-remove-all-filter`
    - element does not work in NG environment

## CHANGE
- `core`
    - changed search result field `articleNumberSearch` (type: `Boolean`, introduced in FF NG) to `resultArticleNumberStatus` (type: `String`, compliant with FF versions prior to FF NG) in NG environment


# 3.15.1
## FIX
- `ff-suggest`
    - added missing `hidden` attribute to empty sections

## IMPROVE
- `ff-record-list`
    - Introduced `infinite-scroll-container` attribute. It allows users to explicitly specify the scroll container that contains the record list. If omitted, WebComponents will try to automatically detect the most suitable container.


# 3.15.0
## ADD
- `ff-asn`
    - introduced `topic` property that allows subscription to a custom topic

## FIX
- `core`
   - `globalCommunicationParameter` can now be reassigned in the `factfinder` instance
- `ff-record-list`
   - fixed infinite scrolling not working in some rare scenarios when no valid scrollable container was found
- `ff-checkout-tracking` and `ff-checkout-tracking-item`
    - `channel` attribute of `ff-checkout-tracking-item` is now used correctly for tracking requests
    
## IMPROVE
- `ff-single-word-search` and `ff-single-word-search-record`
    - migrated to Lit-Element

## DEPRECATE
_Usage of these features is no longer recommended. They are going to be **removed** in a future version._
- `ff-checkout-tracking`
    - the `records` property is redundant because it requires JavaScript to be used. If you need to manually do checkout tracking, please refer to [Tracking with JavaScript](https://web-components.fact-finder.de/documentation/3.x/tracking-with-js)


# 3.14.1
## FIX
- `ff-navigation`
    - navigation did not render at all


# 3.14.0
## ADD
- new element `ff-slider-one-touch`

## FIX
- `core`
    - `navigation` event callbacks (i.e. `success`, `fail` and `always`) are now properly called on navigation frame fetch
- `ff-record-list`
    - infinite scrolling is now working correctly with `[data-container="infinite-scroll-placeholder"]` added
    - SSR product list can be updated when appending new records. Previously an error was thrown caused by missing template string

## DEPRECATE
_Usage of these features is no longer recommended. They are going to be **removed** in a future version._
- `ff-record-list` and `ff-record`
    - the `stamp-always` attribute is now deprecated. Changes in record data is now detected in a more sophisticated manner making indiscriminate re-rendering through `stamp-always` redundant


# 3.13.0
## ADD 
- `ff-record-list`
    - now supports server side rendering through the `ssr` attribute

## FIX
- `ff-navigation` and `ff-header-navigation`
    - navigation search request is now encoded properly in NG environment
    - elements are now working in IE in NG environment

## IMPROVE
- `ff-slider-control`
    - `disable-input-fields` uses native HTML `disabled` attribute to disable slider input field
- `ff-loading-spinner`
    - migrated to Lit-Element


# 3.12.1
## FIX
- `factfinder.common`
    - `dictToParameterString` is now filtering out functions and objects
- `ff-header-navigation`
    - event parameters are now encoded correctly before dispatching when in NG environment

## IMPROVE
- `ff-suggest` and `ff-suggest-item`
    - migrated to Lit-Element

## DEPRECATE
_Usage of these features is no longer recommended. They are going to be **removed** in a future version._
- `ff-searchbox.hidesuggestOnblur`
    - renamed to `hideSuggestOnblur`, corresponding attribute `hidesuggest-onblur` renamed to `hide-suggest-onblur` accordingly


# 3.12.0
## ADD
- `ff-checkout-tracking-item`
    - added new optional attribute `channel`. Use it to send the tracking request to a channel different from the one defined in `ff-communication`

## FIX
- `ff-products-per-page-*`
    - default product per page value can now be selected again after changing to different value
- `ff-asn-group`
    - modifications of an element that is used as a `filterSearch` template done after the component is initialized don't influence consecutive ASN rendering anymore
- `ff-slider-control`
    - fixed `submit-on-input` property to enable automatic input submit
    - added `disable-input-fields` property do disable input fields for min and max slider values
- `ff-slider`
    - parameter `page` is not sent anymore which was causing incorrect records rendered when `ff-record-list` has been used in combination with `infinite-scrolling`
    
## IMPROVE
- `ff-search-feedback`
    - migrated to Lit-Element


# 3.11.5
## FIX
- `tracking`
    - `event.always` is now called only if it is defined and is of type `function`
- `ff-record-list`
    - fixed a bug where `ff-record-list` throws `Cannot read property replace of undefined` when nested inside another component and created via JavaScript at runtime

## IMPROVE
- `core`
    - event objects now have a `cancel` method which can be used when a dispatched event should not cause a request to be sent to FACT-Finder
- `ff-communication`
    - event dispatched automatically by `ff-communication` with added `searchImmediate` attribute will now receive property `searchImmediate` equal to true
- `ff-asn`
    - now supports `subscribe` property


# 3.11.4
## FIX
- `ff-asn-group-slider`
    - fixed setting minimum (or NaN) value in input[data-control='1'] not clearing the filter for some configurations
- `ff-suggest-item`
    - now correctly redirects when in NG environment

## IMPROVE
- `ff-navigation`
    - implemented handling of changes to the `subscribe` property after the component has been initialized
- `ff-communication`
    - removed unused property `async-facets`
- `ff-asn-group`
    - removed unused property `lazy-load`
- `ff-searchbox`
    - `before-search` event is now bubbling
- `ff-searchbutton`
    - now emits `before-search` event when clicked
- if no default product per page value is set, the first one from the list will be used as `origPageSize` in click tracking


# 3.11.3
## FIX
- `ff-suggest-item`
    - click on suggest item now correctly targets NG API where applicable
- category path is now correctly created in navigation tracking while using NG


# 3.11.2
## FIX
- `ff-asn`
    - fixed `[data-container="removeFilter"]` not working for some FACT-Finder configurations


# 3.11.1
## FIX
- `ff-slider-control`
  - `currency-fields` are now used to detect the price type. Using field roles still works and can be used
- `ff-communication`
    - fixed a bug where http parameters were duplicated when using `add-params` attribute
    - fixed a bug where `parameter-whitelist` was only working when `only-search-params` was set

## IMPROVE
- `ff-communication`
    - `only-search-params` will now keep `query`, `filter`, `sort`, `page` and `productsPerPage` in the URL in addition to parameters specified in `parameter-whitelist`
    - default `parameter-whitelist` value was changed from "query,filter" to "" (empty string)


# 3.11.0
## ADD
- `core`
    - additional parameters: `factfinder`, `eventAggregator` and `resultDispatcher` are now accessible from the event object dispatched at `ffReady`
- `ff-asn-remove-all-filter`
    - introduced new `keep-category-path` property that preserves category filters

## FIX
- `ff-asn-group-element`
    - fixed images not being displayed when used in selected item template
- `ff-communication`
    - search result is retrieved from server on every page load when `search-immediate` parameter is set
    - fixed `use-url-parameter=false` in conjunction with `version=ng` pushing filter and sort parameters to url
    - `add-params` no longer ignores parameters with duplicate names
- `ff-slider`
    - fixed slider deselecting other applied filters
- `ff-filter-cloud`
    - fixed duplication of slider entries
- `ff-checkout-tracking`
    - fixed checkout tracking for NG
- `tracking`
    - fixed `addToCart` tracking for NG - `query` parameter is not sent anymore
- follow-up fix for navigation tracking
     - callback is now executed if categoryPath is not found
- updated internal dependencies and the polyfills to the latest version. This will fix a rare bug which resulted in non functional Web Components with an error message: `Failed to construct CustomElement: The result must not have children`

## IMPROVE
- `ff-communication`
    - improved login tracking by reducing requests sent to FACT-Finder
- `ff-asn-group`
    - `group` is now available for data binding in searchable ASN context `[slot="filterSearch"]`

## DEPRECATE
_Usage of these features is no longer recommended. They are going to be **removed** in a future version._
- `ff-search-feedback`


# 3.10.1
## FIX
- fixed URL encoding of FFNG tracking POST request parameters


# 3.10.0
## ADD
- FACT-Finder NG support
- `ff-communication`
    - new `api` attribute to target NG API version (e.g. `v2`, `v3`)

## FIX
- `ff-record-list`
    - fixed `ff-record-list` renders `ff-record` elements always in its root, regardless of custom siblings and parent
- replacing browser history only when `useBrowserHistory` is enabled
- follow-up fix for navigation tracking
    - certain values in query parameters could cause an invalid request

## DEPRECATE
_Usage of these features is no longer recommended. They are going to be **removed** in a future version._
- `factfinder.communication.FFCommunicationEventAggregator`
    - renamed to `factfinder.communication.EventAggregator`


# 3.9.0
## ADD
- `ff-asn`
    - implemented searchable ASN groups
- `ff-record-list`
    - added `infinite-max-pages` attribute that restricts the maximum number of pages that can be loaded when infinite scrolling is enabled

## FIX
- `ff-searchbox`
    - fix for search text being selected when clicking on an input that already has focus
- `ff-filter-cloud`
    - fixed alphabetical sorting of the filter names
- `ff-onfocus-suggest`
    - fixed component not changing suggestions when hovering the search term or selecting it with arrow keys
- defer initial calling of listener added through `ResultDispatcher.addCallback` the same way listener of `ResultDispatcher.subscribe` are deferred as described [here](https://web-components.fact-finder.de/documentation/3.x/configuration)
- fixed navigation tracking to create correct `categoryPath`


# 3.8.0
## ADD
- `ff-filter-cloud`
    - added new component to display all selected ASN filters
- `ff-record-list`
    - added attribute `restore-scroll-position`. When navigating back in the browser, this flag scrolls the view to the last clicked `ff-record`. Data of all `ff-record` elements is stored in the browser session. Works particularly well in combination with the `infinite-scrolling` attribute
    - now supporting `infinite-scrolling` in scrollable DOM parents other than `window`
    - added template support for a placeholder element that gets shown for each record that hasn't been fully loaded yet while waiting for a paging request. It defaults to
      ```html
      <div data-container="infinite-scroll-placeholder"></div>
      ```
      and can be customized through providing an element with the attribute `data-container="infinite-scroll-placeholder"`

## FIX
- `ff-searchbutton`
    - fixed a bug where clicking button descendants wasn't triggering the search

## IMPROVEMENTS
- `ff-communication`
    - when navigating back through browser history and attribute `search-immediate` is set, the search result gets restored from browser history if possible. If this is not possible, a new search is triggered as before
- internal updates of search result in the browser history via `history.replaceState` no longer overwrite the full history object but merge it into the current


# 3.7.0
## ADD
- `ff-paging-select`
    - a brand new component that serves the same purpose as `ff-paging-dropdown` but uses the native HTML `select` element

## FIX
- `ff-asn`
    - fixed handling of implicitly selected filters

## IMPROVEMENTS
- `ff-tag-cloud`
    - migrated to Lit-Element
    - the component no longer updates on changes to data-unrelated properties


# 3.6.1
## FIX
- `ff-paging-dropdown`
    - fixed dropdown not rendering its items correctly

## IMPROVEMENTS
- removed Polymer 3 dependencies from components that have already been migrated to Lit-Element
- `ff-record`
    - render record even if client's data is corrupted (the id of the record returned by FACT-Finder is empty)


# 3.6.0
## ADD
- `ff-slider-control`
    - introduced public `submit` method that submits the slider with the current values of `ff-slider-control` inputs
- `ff-communication`
    - added `mustache-delimiters` attribute that allows users to set custom mustache.js delimiters

## FIX
- `ff-breadcrumb-trail`
    - '*' query is hidden by default now when search is triggered from `ff-navigation` or `ff-header-navigation`
- `ff-record-list`
    - removed internal element with selector `.ffw-infinite-scrolling-border` which could be incorrectly placed due to external CSS resulting in endless triggering of new searches

## IMPROVEMENTS
- `ff-asn`
    - migrated to Lit-Element
- `ff-product-detail`
    - migrated to Lit-Element
- redirect is no longer cancelled if bundled tracking request fails


# 3.5.0
## ADD
- `ff-checkout-tracking-item`
     - add optional attribute `price`. When set this value will be used as price for the checkout tracking request to FACT-Finder instead of the internal lookup from [field roles](https://web-components.fact-finder.de/documentation/3.x/field-roles)
- `ff-breadcrumb-trail`
    - added `show-asterisk-query` attribute to determine if '*' query should be visible in the breadcrumb trail
    - '*' query is hidden by default now. Use `show-asterisk-query` attribute to change default behavior

## FIX
- `ff-communication`
    - unregister global `popstate` listener correctly when removed from DOM
- `ff-searchbox`
    - added default template preventing DOMException when created with `document.createElement("ff-searchbox")`
- `ff-paging-dropdown, ff-paging-item, ff-products-per-page-dropdown, ff-prodcuts-per-page-list, ff-products-per-page-select, ff-serachbox, ff-sortbox`
    - fixed DOMException: The result must not have attributes when using angular or `document.createElement()` 

## IMPROVEMENTS
- `ff-template`
    - migrated to Lit-Element
- `ff-communication`
    - skip initial search request triggered by attribute `search-immediate` when navigating back through browser history and the search result can be restored from history
    - don't dispatch empty data when navigating back through browser history


# 3.4.0
## ADD
- `ff-navigation`
    - added property `navigationData` and `subscribe` so that it is possible to cancel automatic subscription and set navigation data via JavaScript as well

## FIX
- fixed bug which could cause data being dispatched before `ffReady` handlers have been invoked
- `ff-searchbox`
    - renamed custom event `before-target` back to `before-search`
- `ff-header-navigation`
    - fixed categories duplication issue when `ff-header-navigation` and `ff-navigation` components are put together within a page (as well as two instances of `ff-header-navigation` or `ff-navigation`)
- `ff-breadcrumb-trail`
    - fixed separator being displayed when there is no data to render the component for
- `ff-asn`, `ff-paging`
    - fixed elements throwing exception `The result must not have attributes` when using them in Angular or with `document.createElement("ff-asn")`

## IMPROVEMENTS
- `ff-slider-control`
    - added more detailed error logging in case of incorrect custom templates
    - removed unused HTML attribute `slot="sliderControls"` from default template which is used when no custom template is specified


# 3.3.2
## FIX
- `ff-navigation`
    - fixed `dom-updated` event firing so that the event is dispatched after all `ff-navigation-item` elements are rendered
- `ff-asn-group-slider`
    - fixed `[data-container="removeFilter"]`-element being shown even though `ff-asn-group-slider` is collapsed. Note that the `[data-container="removeFilter"]`-element is now a child of the `.ffw-wrapper`-element making it consistent with `ff-asn-group`
- fixed a bug where single-hit-redirect was performed for non-exact searches

## IMPROVEMENTS
- `ff-campaign-feedbacktext`
    - added default template `{{text}}`
    - added property `campaignData` so the campaign to be displayed can be set through JavaScript
- `ff-campaign-advisor`
    - works now out of the box without any custom template
    - added property `campaignData` so the campaign to be displayed can be set through JavaScript


# 3.3.1
## FIX
- removed redundant additional filter request caused by `ff-asn-group-element`


# 3.3.0
## ADD
- `ff-sortbox-select`
    - users can now specify the `<select>` element in custom templates

## FIX
- `ff-checkout-tracking`
    - fixed error in `trackCheckoutItems` method
- `ff-asn-group-slider`
    - fixed slider group being initially expanded although its template does not provide the attribute `opened`
- `ff-slider`
    - removed default styles `border-radius: 10px;` and `margin-top: -4px;` with the selector `ff-slider [slot^="slider"]` as they were too invasive (were introduced in `3.1.1`)
- `ff-suggest-item`
    - fixed query text highlighting when the query contains a space or a single character word (HTML markup is no longer displayed in place of text)

## CHANGE
- removed shadow DOM of all elements (except `ff-campaign-advisor-answer`. This is planned to be included in the next release)
    - `ff-tag-cloud`
        - use CSS selector `ff-tag-cloud .ffw-tagCloudContainer` instead of `--tag-cloud-container` mixin
        - use CSS selector `ff-tag-cloud .ffw-tagCloudLink` instead of `--tag-cloud-link` mixin
    - `ff-search-feedback`
        - use CSS selector `ff-search-feedback .ffw-caption` instead of `--caption-mixin` mixin
        - use CSS selector `ff-search-feedback .ffw-content` instead of `--content-mixin` mixin
- removed inclusion of [ShadyCSS](https://github.com/webcomponents/shadycss) into the bundle.


# 3.2.0
## ADD
- `ff-searchbox`
    - added `show-asterisk-query` attribute to determine if '*' query should be visible
    - '*' query is hidden by default now. Use `show-asterisk-query` attribute to change default behavior

## FIX
- `ff-asn-group-element`
    - reverted `selected` attribute's type to `Boolean` which was accidentally changed in a previous version

## CHANGE
- `ff-breadcrumb-trail`
    - migrated to Lit-Element
- `ff-breadcrumb-trail-item`
    - `clone` function marked as deprecated (to be removed with next breaking changes release)


# 3.1.1
With this release all known issues from the `3.0.0` release have been resolved.

## FIX
- `ff-asn`
    - default templates for `ff-asn-group` and `ff-asn-group-slider`
- `ff-header-navigation`
    - attribute `group-count` is no longer ignored when used together with `hide-empty-groups`

## CHANGE
- `ff-asn-group`
    - removed redundant `<div>` (default detailed links container)
- `ff-asn-remove-all-filter`
    - migrated to Lit-Element
- `ff-compare`
    - migrated to Lit-Element
- cleaned up internal browser history handling of `search-immediate` flag


# 3.1.0
## ADD
- new element `ff-product-teaser-campaign-processor` which can be added within `ff-middleware`

## FIX
- `ff-record-list`
    - paging request during infinite scrolling sometimes overwrites current records instead of appending to them

## CHANGE
- `ff-navigation`
    - migrated to Lit-Element
    - no more need to specify `slot="item"` attribute in `ff-navigation-item` HTML template


# 3.0.1
## FIX
- `ff-slider`
    - fixed issue involving changes not being pushed to browser history when previous search was triggered by `search-immediate` attribute on `ff-communication`
- `ff-asn-group`
    - fixed bug making "show more" and "show less" buttons appear at the same time
    - fixed implementation of native select box
- `ff-asn-group-slider`
    - "removeFilter" container template is now being picked properly when placed outside of `ff-slider-control`
- `ff-asn`
    - fixed removing filter, where `groupName` and `associatedFieldName` have spaces


# 3.0.0
## New Boilerplate
```html
...
    <script src="../bower_components/ff-web-components/dist/vendor/custom-elements-es5-adapter.js"></script>
    <script src="../bower_components/ff-web-components/dist/vendor/webcomponents-loader.js"></script>
    <script defer src="../bower_components/ff-web-components/dist/bundle.js"></script>
</head>
```

We already migrated our demos project in the release/3.0 branch: https://github.com/FACT-Finder-Web-Components/demos/tree/release/3.0

## ADD
- `ff-communication`'s boolean properties with `false` value can be declared as DOM element's attributes explicitly: `<ff-communication />` is equivalent to `<ff-communication search-immediate="false" />`

## FIX
- `ff-onfocus-suggest` left arrow navigation fix for rows that contain more than 2 elements (the closest element is now selected)

## CHANGE
- internal rewrite from [Polymer 1](https://www.polymer-project.org/1.0/docs/devguide/feature-overview) to [Polymer 3](https://www.polymer-project.org/3.0/docs/devguide/feature-overview)
- internal rewrite to use [LitElement](https://lit-element.polymer-project.org) as a base class instead of PolymerElement in the WebComponents
- logging format improvements
- replaced all `tap` events with `click` events
- removed all CSS mixins, use regular CSS selectors instead. See migration guide for details

## BREAKING
- The way of including the Web Components scripts has changed. See [Installation](https://web-components.fact-finder.de/documentation/install-dist) for the right way to include the scripts
- Aligning with the current trend we no longer support [Bower](https://bower.io/). As a replacement you can use [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/lang/en/)
- `ff-searchbox`
    - extending built-in HTML elements is not supported anymore. Hence use `<ff-searchbox>` tag with mandatory `<input />` tag inside instead of `<input is="ff-searchbox" />`
    - if you don't want to use the first `input` tag within `<ff-searchbox>`, you can use `SearchBox.resetInput(selector)` to set the input field
- `ff-searchbutton`
    - extending built-in HTML elements is not supported anymore. Hence use `<ff-searchbutton>` tag with mandatory `<button />` tag inside instead of `<button is="ff-searchutton" />`
    - if you don't want to use the first `button` tag within `<ff-searchbutton>`, you can use `SearchButton.resetInput(selector)` to set the button
- `ff-asn-group`
    - deprecated attribute `laszy-load` was replaced by `lazy-load`
    - use `<div slot="groupCaption" ...>` instead of `<div data-container="groupCaption" ...>`
    - `ff-asn-group-element`s no longer replace `<div data-content="detailedLinks">`, but instead get nested inside now
    - `ff-asn-group-element`s no longer replace `<div data-content="hiddenLinks">`, but instead get nested inside now
- `ff-asn-group-element`
    - use `<div slot="selected" ...>` instead of `<div data-selected ...>`
    - use `<div slot="unselected" ...>` instead of `<div data-unselected ...>`
- `ff-asn-group-slider`
    - use `<div slot="groupCaption" ...>` instead of `<div data-container="groupCaption" ...>`
- `ff-slider`
    - use `<div slot="slider1" id="slider1" ...></div>` instead of `<div data-slider="1" ...></div>`
    - use `<div slot="slider2" id="slider2" ...></div>` instead of `<div data-slider="2" ...></div>`
- `ff-products-per-page-item`
    - removed `clone` method
- `ff-sortbox`
    - introduced new container `<div class="ffw-selected-container">`. This container is always visible and contains the selected `ff-sortbox-item`
    - `key` for _Relevance_ changed from `key="null.desc"` to `key="ff.relevance"`
- `ff-sortbox-item`
    - renamed CSS class `selected` to `ffw-selected`
    - renamed CSS class `showSelected` to `ffw-showSelected`
- `ff-paging-item`
    - `productsPerPageItem` property was renamed to `pagingItem`
- `ff-paging-set`
    - removed `hide()` and `show()` functions, use `hideSelf()` and `showSelf()` instead
- `ff-navigation`
    - removed shadow DOM
- removed `ff-carousel` from the library

## KNOWN ISSUES
- `ff-asn`
    - "removeFilter" element does not work in some scenarios
    - no default templates for group and slider. Omitting `ff-asn-group` and `ff-asn-group-slider` causes errors. Always specify them for correct functioning
    - the following minimal setup is recommended
        ```html
        <ff-asn>
            <ff-asn-group for-group="all" opened>

                <ff-asn-group-element>
                    <div slot="selected">
                        <span>{{element.name}}</span>
                    </div>
                    <div slot="unselected">
                        <span>{{element.name}}</span>
                    </div>
                </ff-asn-group-element>

                <div slot="groupCaption" class="groupCaption">{{group.name}}</div>

                <div data-container="detailedLinks">
                    <div data-content="detailedLinks"></div>
                </div>
                <div data-container="showMore">Show More</div>

                <div data-container="hiddenLinks">
                    <div data-content="hiddenLinks"></div>
                </div>
                <div data-container="showLess">Show Less</div>

                <div class="resetFilter" data-container="removeFilter">Reset Filter</div>
            </ff-asn-group>

            <ff-asn-group-slider opened>
                <div slot="groupCaption" class="groupCaption">{{group.name}}</div>

                <ff-slider-control submit-on-input="true">

                    <ff-slider step-size="1" submit-on-release="true">
                        <div slot="slider1" class="sliderBtn cursorPointer"></div>
                        <div slot="slider2" class="sliderBtn cursorPointer"></div>
                    </ff-slider>

                    <div slot="sliderControls" style="display: flex;justify-content: space-around;align-items: center">
                        <input data-control='1' style="width: 60px;">
                        <span style=" width: 20px; height: 2px; background-color: black;display: inline-block"></span>
                        <input data-control='2' style="width: 60px;">
                    </div>

                    <div class="resetFilter" data-container="removeFilter">Reset Filter</div>
                </ff-slider-control>
            </ff-asn-group-slider>
        </ff-asn>
        ```

# 3.0.0-pre-release-2
## ADD
- `ff-communication`'s boolean properties with `false` value can be declared as DOM element's attributes explicitly: `<ff-communication />` is equivalent to `<ff-communication search-immediate="false" />`

## FIX
- `ff-onfocus-suggest` left arrow navigation fix for rows that contain more than 2 elements (the closest element is now selected)

## CHANGE
- internal rewrite to use [LitElement](https://lit-element.polymer-project.org) as a base class instead of PolymerElement in the WebComponents
- logging format improvements
- replaced all `tap` events with `click` events
- removed all CSS mixins, use regular CSS selectors instead. See migration guide for details

## BREAKING
- `ff-asn-group`
    - deprecated attribute `laszy-load` was replaced by `lazy-load`
    - `ff-asn-group-element` no longer replace `<div data-content="detailedLinks">`, but instead get nested inside now
    - `ff-asn-group-element` no longer replace `<div data-content="hiddenLinks">`, but instead get nested inside now
- `ff-products-per-page-item`
    - removed `clone` method
- `ff-sortbox`
    - introduced new container `<div class="ffw-selected-container">`. This container is always visible and contains the selected `ff-sortbox-item`
    - `key` for _Relevance_ changed from `key="null.desc"` to `key="ff.relevance"`
- `ff-sortbox-item`
    - renamed CSS class `selected` to `ffw-selected`
    - renamed CSS class `showSelected` to `ffw-showSelected`
- `ff-paging-item`
    - `productsPerPageItem` property was renamed to `pagingItem`
- `ff-paging-set`
    - removed `hide()` and `show()` functions, use `hideSelf()` and `showSelf()` instead
- `ff-navigation`
    - removed shadow DOM
- removed `ff-carousel` from the library

# 3.0.0-pre-release-1
This the preview release of our next major update. During the next couple of weeks we are going to upgrade all our internal projects to use our 3.0.0 release.
We expect possible bug fixes during this process but our 3.0 release is feature complete compared to our current version 1.2.13 (31.10.2018). The main difference is that we are now compatible with the current native implementation of Webcomponents and therefore we have a smaller JS bundle and a faster execution.

## New Boilerplate
```html
...
    <script src="../bower_components/ff-web-components/dist/vendor/custom-elements-es5-adapter.js"></script>
    <script src="../bower_components/ff-web-components/dist/vendor/webcomponents-loader.js"></script>
    <script defer src="../bower_components/ff-web-components/dist/bundle.js"></script>
</head>
```

We already migrated our demos project in the release/3.0 branch: https://github.com/FACT-Finder-Web-Components/demos/tree/release/3.0

## CHANGE
- internal rewrite from [Polymer 1](https://www.polymer-project.org/1.0/docs/devguide/feature-overview) to [Polymer 3](https://www.polymer-project.org/3.0/docs/devguide/feature-overview)

## BREAKING
- The way of including the Web Components scripts has changed. See [Installation](https://web-components.fact-finder.de/documentation/install-dist) for the right way to include the scripts
- Aligning with the current trend we no longer support [Bower](https://bower.io/). As a replacement you can use [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/lang/en/)
- `ff-searchbox`
    - extending built-in HTML elements is not supported anymore. Hence use `<ff-searchbox>` tag with mandatory `<input />` tag inside instead of `<input is="ff-searchbox" />`
    - if you don't want to use the first `input` tag within `<ff-searchbox>`, you can use `SearchBox.resetInput(selector)` to set the input field
- `ff-searchbutton`
    - extending built-in HTML elements is not supported anymore. Hence use `<ff-searchbutton>` tag with mandatory `<button />` tag inside instead of `<button is="ff-searchutton" />`
    - if you don't want to use the first `button` tag within `<ff-searchbutton>`, you can use `SearchButton.resetInput(selector)` to set the button
- `ff-asn-group`
    - use `<div slot="groupCaption" ...>` instead of `<div data-container="groupCaption" ...>`
- `ff-asn-group-element`
    - use `<div slot="selected" ...>` instead of `<div data-selected ...>`
    - use `<div slot="unselected" ...>` instead of `<div data-unselected ...>`
- `ff-asn-group-slider`
    - use `<div slot="groupCaption" ...>` instead of `<div data-container="groupCaption" ...>`
- `ff-slider`
    - use `<div slot="slider1" id="slider1" ...></div>` instead of `<div data-slider="1" ...></div>`
    - use `<div slot="slider2" id="slider2" ...></div>` instead of `<div data-slider="2" ...></div>`
- `ff-carousel`
    - removed `getCurrentSlide` method, use `currentSlide` property directly instead
    - removed `getMaxSlides` method, use `maxSlides` property directly instead

#1.2.13
## ADD
- new element `ff-sortbox-select`
- new element `ff-products-per-page-select`
- new elements `ff-middleware` and `ff-multi-attribute-parsing`. These can be used to configure how multi-attribute fields in the FACT-Finder response shall be parsed in order to access their values more easily. Alternatively, the same configuration is also possible with plain JavaScript. See https://web-components.fact-finder.de/api/ff-middleware#tab=docs for details
- for a better debugging experience `ff-header-navigation` logs now when it hides 2nd layer navigation elements without 3rd layer children. If you want to show 2nd layer navigation without 3rd layer children, you can set the attribute `hide-empty-groups="false"`

## FIX
- `ff-asn-group-slider` does not hide anymore when its `absoluteMinValue` is `0`
- CTRL + click now opens links from elements with `data-redirect` (click tracking) attributes in a new tab
- clicking history back redirects to previous page now when immediate search is on, there is no need to click twice
- in addition to left mouse clicks also CTRL+LMB, SHIFT+LMB and MMB are now tracked on elements with `data-redirect` attribute

## CHANGE
- `query` parameter is no longer included in navigation requests

# 1.2.12
## BREAKING
- new `<a>` elements in `ff-header-navigation` are likely to break styling
- the `navigation` event emitted by `factfinder.communication.ResultDispatcher` now passes an array of navigation elements grouped by `clusterLevel` instead of a flat array of the first level of elements

## ADD
- `ff-header-navigation` now renders `<a>` elements to allow right-click navigation. `href`'s are customizable. Also see breaking changes!
- log warning about improperly used Boolean properties
- `ff-campaign-redirect` now has a Boolean attribute `relative-to-origin` to optionally enable FACT-Finder redirect campaigns to be configured with relative destination urls

## FIX
- the `count` parameter in tracking requests now always defaults to 1 when not provided explicitly
- `ff-campaign-redirect` now immediately redirects preventing rendering of content
- do never provide master ID instead of tracking ID in recommendation click tracking
- fix `ff-onfocus-suggest` component, which wasn't shown due to an internal error
- `ff-campaign-shopping-cart` now respects comma separated values

## CHANGE
- navigation elements passed by the `navigation` event emitted by `factfinder.communication.ResultDispatcher` now have a `__SUB_ELEMENTS__` property containing all immediate child elements
- `ff-communication` registers with the `WebComponentsReady` event to call `factfinder.communication.ResultDispatcher.startDispatching()`. This is necessary due to a change in ff-core which now prevents search responses from going unnoticed by Web Components that are initialized too late. `ff-similar-products` and `ff-recommendation` combatted this behaviour by sending an extra request, which they no longer do
- `ff-communication` search-immediate does now invoke the search much earlier than before. Dispatching occurs on `WebComponentsReady` event.

1.2.11
FIX
fixed navigation tracking when using use-url-params="false"

1.2.10
ADD
log information about missing fieldRoles when localizing currencies
log information about missing configuration
log information about missing fieldRoles on tracking requests

FIX
fixed a tracking bug where origPageSize could be calculate wrong

CHG
data-redirect does now use an imperative event listener to prevent accidental overrides to onclick which could cause tracking request to be aborted before tracking succeeds

Meaningful notes:
we removed a behavior from the tracking class, where sending a tracking request was setting the global channel for all elements

1.2.9
ADD
boolean attribute "disable-auto-expand" in ff-asn-group and ff-asn-group-slider which will prevent asn groups with active filters from expanding automatically
FIX
ff-communication currency-min/max-digits functionality restored
fixed a bug where campaigns were disappearing after changing page or sort
fixed a bug where currency symbols were not appearing for shopping cart campaign pushed products

1.2.8
fixed an error related to recommendationClick tracking on product detail pages.
fixed a rare bug where similar products and recommendations are not displayed on first request
ensure redirect happens if tracking request fails

1.2.7
See https://github.com/FACT-Finder-Web-Components/ff-web-components/releases/tag/1.2.7

1.2.7-pre-release-23
FIX
Fixed a bug where currencies were not saved to history and therefore were lost
If the JSON response is too big for the browser history a mock object is pushed to the history which is used to send a new request to FACT-Finder in order to retrieve the old response.

1.2.7-pre-release-22
CHG
ff-slider wrapper div#sliderX got a min-width: 1px in order to prevent slider which occur if the wrapper or the [data-slider] element have a width of 0px
FIX
ff-slider-control input are not updating the slider position

1.2.7-pre-release-21
ADD
string attribute <ff-communication sort-url-parameters-alphabetically="true"> which will cause all http parameters and the related parameter values to be alphabetically sorted
boolean attribute <ff-communication async-facets> which will cause the facets to be rendered after the records are rendered

1.2.7-pre-release-20
FIX: appending http parameters without a value doesn't cause an error anymore

1.2.7-pre-release-19
CHG: ff-slider element does now encode special characters like ~ or ä in parameter names
FIX: <ff-communication use-url-parameter="false"> does now respect all events. Before it could happen that url parameters were pushed by accident.

1.2.7-pre-release-18
HOTFIX: fixed a regex issue regarding suggest query highlighting introduced in 1.2.7-pre-release-16

1.2.7-pre-release-17
CHG: search requests with custom topics won't update the currentSearchResult property and the url parameters
ADD: new ff-checkout-tracking element

1.2.7-pre-release-16
FIX: wrong unit when using <ff-communication currency-code=""> for slider-control inputs
FIX: suggest highlights only one word when searching for multiple words
FIX: ff-suggest-item query highlighting does now properly escape special characters
FIX: jumping slider buttons

1.2.7-pre-release-15
FIX: ff-suggest is not rendered when detached and attached again after initialization.
FIX: currency-code="CODE" currency-country-code="CODE" does now respect multi values like: 100.00 - 150.00
FIX: ASN groups wrong order
CHG: ff-slider-control does now update currencies when group changes -> before only on initialization

1.2.7-pre-release-14
FIX: ff-asn-group hiddenLinks are not rendered when detailedLinks is set to 0
FIX: remove ff-slider log
ADD: ff-record/ff-record-list stamp-always attribute
     By default ff-record does not stamp the dom if the old recordData and the new recordData dont differ by id record.id !== record.id
     If you set the Boolean stamp-always attribute the dom is always stamped even if the id's dont differ (<ff-record-list stamp-always>...</...)
     ff-record-list will always set stamp-always on its ff-record elements

1.2.7-pre-release-13
ADD: ff-suggest-item and ff-asn-group-element are now supporting data-image="{{myOwnBindign}}"

1.2.7-pre-release-12
ADD: <option> element does now support data binding when using <ff-asn-group select-box="true">

1.2.7-pre-release-11
CHG: dispatch campaigns on paging events
CHG: do not update records in ff-record-list if the dispatched records are the same as the old records

1.2.7-pre-release-10
ADD: currency-min-digits and currency-max-digits to ff-communication for currency localization configuration

1.2.7-pre-release-9
FIX: currency-code="GBP" and currency-country-code="en-GB" are now working on page 2 and following

1.2.7-pre-release-8
FIX: fixed mustache.js bug when using requirejs introduced with the upgrade to mustache 2.3.ß
FIX: removed a console.log

1.2.7-pre-release-7
ADD: possibility to localize multiple price fields with the "currency-fields" attribute on ff-communication

1.2.7-pre-release-6
ADD: add only-search-params and parameter-whitelist to ff-communication

1.2.7-pre-release-5
CHG: use-url-parameter="false" in conjunction with keep-url-params="all" does now prevent webcomponents from removing custom http parameter

1.2.7-pre-release-4
BUG: fix slider hide bug when min=max value

1.2.7-pre-release-3
CHG: remove infiniteBorder div in ff-record-list when no infinite-scrolling is active
CHG: ff-slider uses now selectedMin/Max as absoluteMin/Max if selected > absolute

1.2.7-pre-release-2
ADD: add category filtering with filterPath and pretty urls
ADD: ff-slider: slider resets now the filter if values are back to absolute min/max
ADD: ff-asn-group gets select-box (<select>) for hiddenLinks as alternative
FIX: topic "result" is now dispatched again on ppp, paging and sort events

1.2.7-pre-release-1
FIX: fix a bug where unit is not shown at first request

Latest 1.2.6
FIX: fix bug in ff-paging-dropdown when dispatching result of new products-per-page
FIX: fix check for deeplink on on-record-redirect
FIX: fix wrong max width calculation for ff-slider
FIX: ff-communication iphone wrong null check when using single-hit-redirect-base-path
fix: fixed a transition bug where a transition was executed with an transition duration of 0s instead of its original transition-duration value

Style Changes
CHG: ff-asn-group-element - in some cases a style="display: inline;" was added to the [data-selected] [data-unselected]
CHG: ff-asn-group-element - we've changed the wrapping divs (#selected, #unselectd) display property to display: inline-block instead of display: block; If you want to revert the changes use the new mixins --unselected-container and --selected-container to set the properties back to block

1.2.5
FIX: ff-onfocus-suggest replace nodelist forEach with normal for-loops
FIX: reset ff-carousel to slide to first slide after the records have changed
CHG: make filtering without clusterLevel possible again
ADD: add single-hit-redirect-base-path to ff-communication for redirect to deeplink when just 1 record is in result
FIX: fixed a rare breadcrumb bug

1.2.4
FIX: fixed slider control bug where undefined was set as a value when no unit was configured
FIX: fixed a bug where the right slider could cross the right border
FIX: error ref_node to insertBefore is not a child of this node

1.2.3
BREAKING CHANGE: we've untied the ff-slider-control templates completely to allow more layout flexibility. This may break you styles because the html order is now kept like supplied.
ADD: usePerso attribute to ff-recommendation
ADD: ff-slider-control input element attributes are now stamped with the template engine like: <input type="text" data-control='1' data-read-only-suffix="{{group.unit}}"/>
FIX: fixed a tracking issue in pushed products campaigns
CHG: rename mixin's for ff-carousel legend to bullets and add record observer
FIX: fixed occasional bug where right slider jumps to the left side and cant be moved afterwards

1.2.2
FIX: ff-asn-group-slider is not opened when group filters are active
ADD: ff-communication does now support 2 new attribute currency-code="GBP" currency-country-code="en-GB" all prices can now automatically be rewritten according to this new settings
ADD: improve validation on slider-control input fields
ADD: add option "all" for keep-url-params which will keep all non FACT-Finder related params
FIX: timing issues on out of order suggest results
ADD: add suggest-delay to ff-searchbox to customize the react time of the input.
FIX: log error if image data is not in record instead of sending a request with /undefiend
ADD: infinite-scroll-margin to ff-record-list
FIX: added new regex for query param

1.2.1
FIX: fixed ff-paging-item changes type attribute to currentLink
FIX: query param was encoded twice in tracking requests
FIX. ff-searchbox value was shown url encoded when loading the page the first time
ADD: add a data-anchor attribute to the ff-record to resolve hyper links
ADD: add 'data-track-count' to TrackingBehavior
FIX: don't dispatch to the breadcrumb after a paging, ppp or sort

1.2.0
ADD: ff-slider-control introduces new mixins
ADD: ff-paging-item does now set the css class disabled when it is not active
FIX: fixed a bug for ff-record data-redirect where some data-redirect targets other than _self could lead to flaky click tracking
FIX: pushed wrong url to browser history when using a html <base> tag
ADD: ff-paging-dropdown element
ADD: Backwards compatibility for FF < 7.3 and "productName" ff-suggest-item click
FIX: broken layout of container in ff-header-navigation
ADD: add "ff-asn-remove-all-filter" element
ADD: suggest-product-record event to ff-suggest which contains the product fetched by the REST call on a suggest productName click
ADD: ff-suggest-item uses the REST get records API to fetch a product on a suggest productName click
ADD: getRecordsUrl property on ff-communication
CHG: core Dispatcher and custom topics
FIX: ignore 'ignorePage' lazy check on searchImmediate
CHG: core Distapcher and custom topics
ADD: infinite scrolling to ff-record-list
CHG: add dynamic slots and change the layout of the container in ff-header-navigation
CHG: don't dispatch asn on a sort, paging or ppp event
ADD: add custom urls to ff-communication
FIX: ASN filter did not consider the ClusterLevel of an element

1.1.10
FIX: Overriding the default action of the ff-suggest-item click

1.1.9
FIX: add fallback for not supported localStorage in Safari inkognito mode

1.1.8
FIX: fix a bug where in Safari 10.1 ff-asn-groups collapse and are not openable

1.1.7
FIX: ff-asn crashs without configured slider

1.1.6
CHG: removed blank between numerical values of slider filter values as the FF-UI diagnostic search can't handle them
CHG: change ff-paging inheritance behavior for showOnly property
FIX: init of ff-asn-group template in ff-asn and asn-group-element template upgrading in ff-asn-group
FIX: ff-asn-group-slider are always shown
CHG: add lazy-rendering for detailedLinks in asn-group
ADD: ff-communication does now send login event when user-id attribute changes. If set, all tracking requests will have the userId as an additional parameter
ADD: ff-communication add sid attribute
CHG: campaign dispatching dose not dispatch 'undefined' to campaigns which are affected.
FIX: set asn-group element 'opened' when group has a selectedElement in searchResult

1.1.5
FIX: shoppingCartCampaign dispatching bug
ADD: ff-search-feedback dont-sho-on-result-changed attribute

1.1.4
FIX: fix suggest 401 bug
FIX: ff-tag-cloud double encoding bug
ADD: ff-suggest-item adds now queryFromSuggest

1.1.3
ADD shopping cart campaign API element (ff-campaign-shopping-cart)
ADD ff-tag-cloud
ADD lazy-load for ff-asn-group
ADD ff-compare element
ADD factfinder.communication.FFCommunicationEventAggregator.addBeforeDispatchingCallback(fn)

1.1.0
ADD: ff-search-feedback element
ADD: ff-campaign-landing-page element
ADD: ff-navigation element
ADD: ff-header-navigation element

1.0.16
fix: console error log on tracking request
fix: recommendation are not displayed

1.0.15
ff-communiction: fixed search-immediate always true when use-seo="true"
ff-slider: fixed encoding issue
ff-breadcrumb-trail-item: does now reflect type attribute
fixed tracking 401 bug

1.0.14
ff-searchbox: fixed on key left right console error when no ff-suggest available
ff-communication: fixed encoding issue when use-seo was set to true
ff-campaign-advisor: fixed polyfill related display bug which caused the advisor question not to show up occasionally in firefox and IE
ff-communication: fixed a bug where setting the version attribute to 7.2 resulted in console log: version ont supported


1.0.12
ff-campaign-advisor bugfix: The ff-campaign-advisor-questions contains now the ff-campaign-advisor-answer as it should be. Therefore the ff-campaign-advisor element is now able to process more than 1 advisor question.
add use-browser-history="true/false" to ff-communication
add use-url-parameter="true/false" to ff-communication
minor improvements

1.0.10 -> 1.0.11
fixed umlaut encoding bug in suggest searchTerms

1.0.9 -> 1.0.10
fixed: search-immediate wasn't occasionally executed in Internet Explorer

1.0.8 -> 1.0.9
ff-asn does now set style="display:none;" at creation time
fixed search-immediate error again

1.0.7 -> 1.0.8
fixed a bug where no tracking request was send on data-redirect
add factfinder.communication.version

1.0.6 -> 1.0.7
fixed onerror-image uncaught exception

1.0.5 -> 1.0.6
Renamed shadow dom css class from container to ff-asn-group-container due to polyfill lack of scoping
Add removeUnresolvedAttribute behavior. It's now possible to prevent FOUC with the [unresovled] attribute on all ff-* elements with visual component
[data-image] attribute is now automatically resolved with the appropriate fieldRole value if possible
ff-sortbox does not change the key anymore when showSelected is true (currentKey + "_showSelected")