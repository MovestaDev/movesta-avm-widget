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

This example creates the widget element in HTML and initializes it via JavaScript.
```html
<div class="movesta-avm-widget"></div>
<script type="text/javascript">
  MovestaAVMWidget.init({
    style: {},
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

| Parameter Name                           | Description                                                 | Default Value                                               |
| ---------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `type`                                   | Widget type, `'inline'` or `'floating'`                     | `'inline'`                                                  |
| `style.spacing`                          | Base spacing, multiples of it are used across the widget    | `'5px'`                                                     |
| `style.transitionFactor`                 | Transition duration factor, set to 0 to disable the effect. | `1`                                                         |
| `style.floatingBoxButtonBackgroundColor` | Button color, in case `type` is set to `'floating'`         | `'#aaa'`                                                    |
| `inputLabelPlacement`                    | Form field label position (`'top'` or `'placeholder'`)      | `'top'`                                                     |
| `stepHeadings`                           | Display heading for each step                               | `true`                                                      |
| `onComplete.type`                        | Completion action type, `'button'` or `'url'`               | (required)                                                  |
| `onComplete.url`                         | Completion redirect URL                                     | (required)                                                  |
| `onComplete.buttonText`                  | CTA button text for `onComplete.type` set to `'button'`     | `'Gå vidare'`                                               |
| `onComplete.estimatePrefix`              | Text before the valuation, e.g. "Värderingen är"            | `null`                                                      |
| `onComplete.showRange`                   | Show valuation range                                        | `true`                                                      |
| `onComplete.showRestart`                 | Show restart button                                         | `true`                                                      |
| `onComplete.headingText`                 | Heading on the valuation page                               | `'Din värdeindikation'`                                     |
| `onComplete.introText`                   | Text above the valuation estimate                           | `null`                                                      |
| `onComplete.promptText`                  | Text below the valuation estimate/range                     | `null`                                                      |
| `termsAndConditions`                     | Link for terms and conditions                               | (required)                                                  |
| `development`                            | Development mode, see below                                 | `false`                                                     |
| `steps.postalAddress.headingText`        | Heading for postal address step                             | `'Var bor du?'`                                             |
| `steps.housingType.headingText`          | Heading for housing type step                               | `'Vilken typ av bostad är det?'`                            |
| `steps.livingArea.headingText`           | Heading for living area step                                | `'Hur stor är bostaden?'`                                   |
| `steps.numRooms.headingText`             | Heading for no rooms address step                           | `'Hur många rum?'`                                          |
| `steps.contactDetails.headingText`       | Heading for contact details step                            | `'Hur når vi dig?'`                                         |
| `steps.contactDetails.introText`         | Text above the contact fields                               | `'Fyll i dina kontaktppgifter och se din värdeindikation.'` |
| `steps.contactDetails.name`              | Ask for customer name                                       | `true`                                                      |
| `steps.contactDetails.phone`             | Ask for customer phone number                               | `true`                                                      |

(All `steps.contactDetails.*` fields can also be set using just `contact.*` but this is deprecated and will be removed in future releases.)

### CSS classes

You can use the following CSS classes to style the widget. There is an example stylesheet in the `examples/` folder.

For better understanding of the DOM and the classes, use the dev console in your browser.

| CSS Class                                        | Description                                                            |
| ------------------------------------------------ | ---------------------------------------------------------------------- |
| `.movesta--avm-widget-root`                      | Widget container                                                       |
| `.movesta--avm-form`                             | AVM form container                                                     |
| `.movesta--step-heading`                         | Form step heading                                                      |
| `.movesta--step-description`                     | Form step description                                                  |
| `.movesta--step-container  `                     | Form step container (input elements)                                   |
| `.movesta--link`                                 | All link elements (anchors)                                            |
| `.movesta--text-field`                           | Text field input                                                       |
| `.movesta--field-label`                          | Form input fields label                                                |
| `.movesta--text-field-container`                 | Text (input) field container                                           |
| `.movesta--button-primary`                       | Primary button (e.g. next, submit)                                     |
| `.movesta--button-secondary`                     | Secondary button (e.g. back)                                           |
| `.movesta--autocomplete-input-with-options`      | Autocomplete input, with options (on top of text field styling)        |
| `.movesta--autocomplete-options-wrapper`         | Autocomplete options wrapper                                           |
| `.movesta--autocomplete-option`                  | Autocomplete option                                                    |
| `.movesta--autocomplete-option-no-street-number` | Autocomplete option without street number                              |
| `.movesta--housing-type-buttons-wrapper`         | Container for the housing type buttons (apartment, townhouse, ...)     |
| `.movesta--housing-type-button`                  | Housing type button                                                    |
| `.movesta--housing-type-button-active`           | Active (selected) housing type button                                  |
| `.movesta--radio-container`                      | Outer container for radio buttons (currently only housing types)       |
| `.movesta--checkbox`                             | Checkbox input (input element)                                         |
| `.movesta--checkbox-container`                   | Container around the input, the empty element and the text label       |
| `.movesta--checkbox-label`                       | Empty element to be used to style a "fake checkbox" if input is hidden |
| `.movesta--checkbox-label-checked`               | Empty element if the checkbox is checked                               |
| `.movesta--form-error`                           | Form input error message, e.g. alphabetic character in number of rooms |
| `.movesta--circular-progress`                    | Loading spinner for form submission                                    |
| `.movesta--valuation-wrapper`                    | Valuation result wrapper                                               |
| `.movesta--valuation-heading`                    | Valuation result heading                                               |
| `.movesta--valuation-intro`                      | Valuation result text (above valuation)                                |
| `.movesta--valuation-footer`                     | Valuation result text (below valuation)                                |
| `.movesta--valuation-estimate`                   | Valuation estimate                                                     |
| `.movesta--valuation-range`                      | Valuation range                                                        |
| `.movesta--valuation-error`                      | Valuation error message (e.g. backend error)                           |


### onComplete Options

There are two options for the `onComplete` parameter, `redirect` and `CTA`:

With `'redirect'`, the user is redirected to the specified URL after successful form submission. 
The valuation result is added as query parameters. 
```javascript
const onCompleteRedirect = {
  type: 'redirect',
  url: 'https://google.com',
  // ...
}
```

With `'CTA'`, the valuation result is displayed in the widget with a configurable CTA button below.
```javascript
const onCompleteCTA = {
  type: 'CTA',
  url: 'https://google.com',
  buttonText: 'Gå vidare',
  // ...
}
```
### Development mode
With `development: true`, requests are sent to a separate development environment, for which separate webhooks can be set up, etc. (see [Get the data](#➡️-get-the-data) below.) Please note:
- *Development mode must be used to submit the form with `localhost` as an origin.*
- *Development mode should be used for testing only, the valuations obtained are low quality and not representative of actual home market values.*


## ➡️ Get the data

The preferred way is to provide a webhook URL to which we will post back the webform data and valuation result. Contact tech@movesta.com for more info.

## 🏁 Examples

See the `examples/` directory for help to get up and running quickly.

## 🔑 Access

To obtain access, please contact tech@movesta.com for more details and pricing information.

## 🚧 Beta Version

This is a beta version of the widget. The focus is to support all frameworks, and a proper npm package will be released in the future.

## 🔗 Links

- [Movesta — Köp med trygghet, sälj utan stress](https://www.movesta.se)
