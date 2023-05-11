# 🏠 Movesta AVM Widget

A third-party integration of [Movesta](https://www.movesta.se)'s automated valuation model for real estate in Sweden. 

Estimate home values as of today using an easy-to-integrate website widget, a great tool for customer acquisition. Shows an estimate and range of the value of homes across Sweden via basic information like location, living area, and number of rooms.

## 📦 Installation

### Step 1: Load the script

The script is hosted under
```
https://cdn.jsdelivr.net/gh/MovestaDev/movesta-avm-widget@<release>/static/movesta-avm-widget.js
```

Please check the [releases/](Releases) section and pick the latest one and replace `<release>` in the URL above.

Plain JavaScript via a `<script>` tag:

```html
<script src="..." type="text/javascript"></script>
```

For usage with React, follow this guide: [4 Ways of Adding External JS Files in ReactJS](https://betterprogramming.pub/4-ways-of-adding-external-js-files-in-reactjs-823f85de3668). A proper npm package will be available in the future.

### Step 2: Create the Widget element

This example creates the widget element and 
```html
<script type="text/javascript">
  const myStyle = {
    fontFamily: 'inherit',
    accentColor: '#03396c',
    accentDark: '#03396c',
  };

  MovestaAVMWidget.init({
    style: myStyle,
    onComplete: {
      type: 'redirect',
      url: 'https://successfulrealtor.se/submitted'
    },
    termsAndConditions: 'https://successfulrealtor.se/terms-of-service'
  })
</script>
```

## ⚙️ Configuration

Note: the dot (.) refers to _nested objects_!

| Parameter Name         | Description                                  | Default Value                   |
|------------------------|----------------------------------------------|---------------------------------|
| `onComplete`           | Form submission action, see below (required) | -                               |
| `termsAndConditions`   | Link for terms and conditions (required)     | -                               |
| `type`                 | Widget type                                  | `'inline'`                      |
| `contact.name`         | Show name form field                         | `true`                          |
| `contact.phone`        | Show phone form field                        |`true`                           |
| `style.accentColor`    | Accent color                                 |`'#2d7a72'`                      |
| `style.accentDark`     | Accent dark color                            |`'#1f5550'`                      |
| `style.accentContrast` | Accent contrast color                        | `'#fff'`                        |
| `style.fontFamily`     | Font family                                  | generic sans-serif font         |
| `development`          | Development mode                             | `false`                         |  

_Development mode_ is intended to be used for testing and development against the non-production AVM endpoint.

### onComplete Options

There are two options for the `onComplete` parameter, `redirect` and `CTA`:

```javascript
const onCompleteRedirect = {
  type: 'redirect',
  url: 'https://google.com',
}

const onCompleteCTA = {
  type: 'CTA',
  url: 'https://google.com',
  text: 'Gå vidare',
}
```

## 🔑 Access

To obtain access, please contact tech@movesta.com for more details and pricing information.

## 🚧 Beta Version

This is a beta version of the widget. The focus is to support all frameworks, and a proper npm package will be released in the future.

## 🔗 Links

- [Movesta — Köp med trygghet, sälj utan stress](https://www.movesta.se)
