# 🏠 Movesta AVM Widget

A third-party integration of Movesta's automated valuation model for real estate in Sweden. 

Estimate home values as of today using an easy-to-integrate website widget, a great tool for customer acquisition. Shows an estimate and range of the value of apartments (lägenhet), detached (villor), townhouses (radhus), and holiday homes (fritidshus) across Sweden via basic information like location, living area, and number of rooms.

## 📦 Installation

Include the widget via a script tag. For usage with React, follow this guide: [4 Ways of Adding External JS Files in ReactJS](https://betterprogramming.pub/4-ways-of-adding-external-js-files-in-reactjs-823f85de3668). A proper npm package will be available in the future.

```html
<!-- <script 
  src="https://cdn.jsdelivr.net/gh/MovestaDev/movesta-avm-widget@development/static/movesta-avm-widget.js"
  type="text/javascript">
</script> -->

<script type="text/javascript">
  const myStyle = {
    fontFamily: 'inherit',
    accentColor: '#03396c',
    accentDark: '#03396c',
  };

  MovestaAVMWidget.init({
    key: 'demo-key',
    style: myStyle
  })
</script>
```

## ⚙️ Configuration

Note: the dot (.) means _nested objects_!

| Parameter Name     | Description                                      | Default Value                                                                                               |
|--------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| `key`                  | API key (required)                               | -                                                                                                           |
| `onComplete`           | Form submission action, see below (required)     | -                                                                                                           |
| `termsAndConditions`   | Link for terms and conditions (required)         | -                                                                                                           |
| `type`                 | Widget type                                      | `'inline'`                                                                                                    |
| `contact.name`         | Show name field                                  | `true`                                                                                                        |
| `contact.phone`        | Show phone field                                 |`true`                                                                                                        |
| `style.accentColor`    | Accent color                                     |`'#2d7a72'`                                                                                                   |
| `style.accentDark`     | Accent dark color                                |`'#1f5550'`                                                                                                   |
| `style.accentContrast` | Accent contrast color                          | `'#fff'`                                                                                                      |
| `style.fontFamily`     | Font family                                      | See DEFAULT_CONFIG fontFamily in the provided information                                                   |

### onComplete Options

Choose and customize one of these two options for the `onComplete` parameter:

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

## 🔑 API Key

To obtain an API key, please contact sales@movesta.com for access and pricing information.

## 🚧 Beta Version

This is a beta version of the widget. The focus is to support all frameworks, and a proper npm package will be released in the future.