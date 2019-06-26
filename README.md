FACT-Finder Web Components
==========================
Paging Select branch (experimental)
-----------------------------------

This branch introduces the `ff-paging-select` element. It provides paging functionality through a native `select` element.

_Note that this feature is at an experimental stage and changes may occur._

### The Paging Select Element

The following listing shows the newly introduced element.

```html
<ff-paging-select>
    <select>
        <option>Page: {{caption}}</option>
    </select>
</ff-paging-select>
```

#### Properties

Property | Type | Required | Default | Element updates on change | DOM Attribute
-------- | ---- | -------- | ------- | ------------------------- | -------------
pagingData | Object | no   | `undefined` | yes                   | _(none)_

This property holds the data that shall be visualized by the element. It has the same structure as the FF response's `searchResult.paging` property.

The equivalent property on `ff-paging` is simply called `paging`.

#### Events

Name | Description
---- | -----------
dom-updated | This event is triggered when the element has received new data and the template for this element and all sub elements have been punched out.

### Default Templates

Default templates are _all-or-nothing_. They are only employed when the `ff-paging-select` element is empty. Anything else is considered a custom template and deactivates default templates.

Default `option` template corresponds to:
```html
<option>{{caption}}</option>
```

Default `select` template corresponds to:
```html
<select>
    <option>{{caption}}</option>
</select>
```

### Example Setup

#### HTML
```html
<ff-paging-select></ff-paging-select>
```

#### Rendered

_Assuming FACT-Finder is set to display 5 links._

Current page: 1
```html
<ff-paging-select>
    <select>
        <option>1</option>
        <option>2</option>
        <option>3</option>
        <option>4</option>
        <option>5</option>
    </select>
</ff-paging-select>
```

Current page: 4
```html
<ff-paging-select>
    <select>
        <option>2</option>
        <option>3</option>
        <option>4</option>
        <option>5</option>
        <option>6</option>
    </select>
</ff-paging-select>
```

#### Setup

```html
<ff-paging-select>
    <option>Page {{caption}}</option>
</ff-paging-select>
```

#### Rendered

```html
<ff-paging-select>
    <select>
        <option>Page 1</option>
        <option>Page 2</option>
        <option>Page 3</option>
        <option>Page 4</option>
        <option>Page 5</option>
    </select>
</ff-paging-select>
```

#### Setup

```html
<ff-paging-select>
    <select class="user-class"></select>
</ff-paging-select>
```

#### Rendered

```html
<ff-paging-select>
    <select class="user-class">
        <option>1</option>
        <option>2</option>
        <option>3</option>
        <option>4</option>
        <option>5</option>
    </select>
</ff-paging-select>
```

#### Setup

```html
<ff-paging-select>
    <select class="user-class">
        <option>Page {{caption}}</option>
    </select>
</ff-paging-select>
```

#### Rendered

```html
<ff-paging-select>
    <select class="user-class">
        <option>Page 1</option>
        <option>Page 2</option>
        <option>Page 3</option>
        <option>Page 4</option>
        <option>Page 5</option>
    </select>
</ff-paging-select>
```

## General Notes

This distribution provides only the build including all dependencies (Polymer 3, Lit Element). If you need to use/include each element separately, please refer to your FACT-Finder Project Developer.

See [web-components.fact-finder.de](http://web-components.fact-finder.de/) for the complete documentation including Get Started, Developer Guide and more.

## Installation

Directly from GitHub via npm.

For latest update:
```
npm i git+https://git@github.com/FACT-Finder-Web-Components/ff-web-components.git#release/BETA-paging-select
```

Specific version via tag:
```
npm i git+https://git@github.com/FACT-Finder-Web-Components/ff-web-components.git#3.4.0-paging-select.1
```

Or via package.json:
```json
"dependencies": {
  "ff-web-components": "git+https://git@github.com/FACT-Finder-Web-Components/ff-web-components.git#release/BETA-paging-select"
}
```
