FACT-Finder Web Components
==========================
NG branch (experimental)
------------------------

This branch introduces Web Components support for the new NG API. To use it, you need the latest version of FACT-Finder **NG**.

_Note that this feature is at an experimental stage and changes may occur._


## Features

The following features are currently supported:
- search
- navigation

More features will be added incrementally.


## Setup

To use Web Components with FACT-Finder NG, simply set the `version` attribute on `ff-communication` to `ng`. The remaining setup is as usual.

```html
<ff-communication url="your.fact-finder-ng.url"
                  version="ng"
                  channel="your-channel"
></ff-communication>
```


## General Notes

This distribution provides only the build including all dependencies (Polymer 3, Lit Element). If you need to use/include each element separately, please refer to your FACT-Finder Project Developer.

See [web-components.fact-finder.de](http://web-components.fact-finder.de/) for the complete documentation including Get Started, Developer Guide and more.


## Installation

Directly from GitHub via npm.

For latest update:
```
npm i git+https://git@github.com/FACT-Finder-Web-Components/ff-web-components.git#release/ALPHA-NG
```

Specific version via commit ID (example ID):
```
npm i git+https://git@github.com/FACT-Finder-Web-Components/ff-web-components.git#bb9762bf
```

Or via package.json:
```json
"dependencies": {
  "ff-web-components": "git+https://git@github.com/FACT-Finder-Web-Components/ff-web-components.git#release/ALPHA-NG"
}
```
