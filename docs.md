[th]: http://twitter.github.io/typeahead.js
[th-docs]: https://github.com/twitter/typeahead.js/blob/master/doc/jquery_typeahead.md

# meteor-typeahead

The [typeahead.js][th] plugin to make your inputs with autocomplete support packaged for meteor applications.

# Table of Contents

* [Features](#features)
* [Usage](#usage)
  * [API](#api)
  * [Datasets](#datasets)
  * [Options](#options)
  * [Events](#events)

## Features

* Support fetching meteor collections as typeahead dataset
* Easy to bind auto-complete suggestions to input using `data-source` attribute
* Allow using meteor template to visualize auto-complete suggestion
* Support most [typeahead.js][th] use cases:
  * Asynchronous data sources
  * Prefetched JSON data source
  * Multiple datasets

## Usage

### API

#### Meteor.typeahead(element, source)

Turns given HTML `<input[type="text"]/>` into a typeahead.

* `element` - is HTML input element.
* `source` - is optional custom data source function with `function(query, callback)` signature where query is `text` entered in the input and `callback` is callback function to  suggestions to show in dropdown.

#### Meteor.typeahead.inject(selector)

Activates typeahead behavior for all elements matched by given CSS `selector`. `selector` parameter defaults to '.typeahead'.

### Datasets

[typeahead.js][th] dataset(s) is specified as data attribute if you don't specify custom data source function in `Meteor.typeahead` call.

* `data-source` - name of function defined as helper for your meteor template with typeahead input. Optionally you could specify `collection.property` to automatically bind given meteor collection to your typeahead input

* `data-sources` - name of tempalte helper function that returns array of typeahead datasets. `data-sets` is alias. Demo application has an example.

### Options

[typeahead.js][th] [options](https://github.com/twitter/typeahead.js/blob/master/doc/jquery_typeahead.md#options) are specified as data attributes in your input element. List of supported attributes:

* `data-highlight` – If `true`, when suggestions are rendered, pattern matches for the current query in text nodes will be wrapped in a `strong` element with `tt-highlight` class. Defaults to `false`.

* `data-hint` – If `false`, the typeahead will not show a hint. Defaults to `true`.

* `data-min-length` – The minimum character length needed before suggestions start getting rendered. Defaults to `1`.

#### Events

Using data attributes you could specify handlers for corresponding typeahead `opened`, `closed`, `selected`, `autocompleted` events. Value of data attribute is name of template helper function to be used as event handler.

* `data-opened` - specifies handler for for `typeahead:opened` event
* `data-closed` - specifies handler for for `typeahead:closed` event
* `data-selected` - specifies handler for for `typeahead:selected` event
* `data-autocompleted` - specifies handler for for `typeahead:autocompleted` event

See also [typeahead docs](https://github.com/twitter/typeahead.js/blob/master/doc/jquery_typeahead.md#custom-events) for custom events.