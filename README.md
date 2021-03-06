# Polymer Snippets for Atom

![banner](http://s12.postimg.org/opgzpvtpp/banner.png)

## Install
Go to `atom > Preferences...` then search for Polymer Snippets in Packages tab.

## Compatibility with Emmet
If you have [Emmet](https://github.com/emmetio/emmet-atom) installed it will clobber the tab completion for HTML snippets. You can follow [this workaround](https://github.com/emmetio/emmet-atom/issues/225#issuecomment-82669798) to get Polymer snippets working again.

## Elements

Type the name of [any `core-*` or `paper-*` element](https://www.polymer-project.org/docs/elements/), then hit `tab` to auto complete. Ex:

![Demo](https://cloud.githubusercontent.com/assets/1066253/6306345/80bc2076-b8e7-11e4-9529-64494eb46540.gif)

## Polymer

### [pe] polymer element

```html
<polymer-element name="${2}" attributes="${3}">
  <template>
    <style>
      :host {
        display: block;
      }
    </style>$4
  </template>
  <script>
    Polymer({

    });
  </script>
</polymer-element>
```

### [pen] polymer element noscript

```html
<polymer-element name="${2}" noscript>
  <template>
    <style>
      :host {
        display: block;
      }
    </style>$4
  </template>
</polymer-element>
```

### [pes] polymer element with external stylesheet

```html
<polymer-element name="$1" attributes="$2">
  <template>
    <link rel="stylesheet" href="$3.css">$4
  </template>
  <script>
    Polymer({
      $5
    });
  </script>
</polymer-element>
```

### [hi] html import

```html
<link rel="import" href="${0}">
```

### [hic] html import core-* element

```html
<link rel="import" href="${1:bower_components}/core-${2}/core-${2}.html">
```

### [hip] html import paper-* element

```html
<link rel="import" href="{1:bower_components}/paper-$2/paper-$2.html">
```

## Web Components

### [tm] template
```html
<template$1>$0</template>
```

### [ce] custom element

```javascript
var ${4:tmpl} = document.querySelector('${5:template}');

var ${1:WidgetProto} = Object.create(HTMLElement.prototype);

${1:WidgetProto}.createdCallback = function() {
  var root = this.createShadowRoot();
  root.appendChild(document.importNode(${4:tmpl}.content, true));
};

var ${2:Widget} = document.registerElement('${3:my-widget}', {
  prototype: ${1:WidgetProto}
});
```

## HTML

### [ph] HTML template with Web Components polyfill

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">

  <title>${1}</title>
  <meta name="description" content="${2}">

  <!-- Mobile -->
  <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">

  <!-- Chrome / Android -->
  <meta name="mobile-web-app-capable" content="yes">
  <meta name="theme-color" content="black">
  <link rel="icon" href="icon.png">

  <!-- Safari / iOS -->
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black">
  <link rel="apple-touch-icon-precomposed" href="apple-touch-icon.png">

  <!-- Web Components -->
  <script>
    if ('registerElement' in document
    && 'createShadowRoot' in HTMLElement.prototype
    && 'import' in document.createElement('link')
    && 'content' in document.createElement('template')) {
      // Native WC support. Do nothing
    } else {
      document.write('<script src="/bower_components/webcomponentsjs/webcomponents.js"><\/script>');
    }
  </script>
</head>
<body unresolved>
  $0
</body>
</html>
```

## CSS

### [sh] ::shadow
```css
::shadow ${2:target} {
  $0
}
```

### [sd] /deep/
```css
/deep/ ${2:target} {
  $0
}
```

### [cn] content::content
```css
${1:content}::content ${2:target} {
	$0
}
```

### [ho] :host
```css
:host$0
```

### [hc] :host-context()
```css
:host-context($0)
```

### [pf] polyfill-next-selector
```css
polyfill-next-selector { content: '${1::host > .foo}'; }$0
```

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## License

[MIT License](http://robdodson.mit-license.org/) © Rob Dodson
