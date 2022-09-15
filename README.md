# Spry Validator Plugin Documentation
This plugin depends on **adobe spry validation open source** and **JQuery version 1.12.4** and above.
<br>
It can validate input types like **(text, integer, email, date, time, credit_card, zip_code, phone_number, social_security_number, currency, real, url, ip, textarea, select, checkbox, radio, password, and password confirmation)** with a super easy and professional way at the same time.
<br>
**And the main feature that it works on forms and any other group of inputs inside a ```div``` container or any other container for AJAX requests or any other logic.**

## Requirements
**1- Including the CSS file:**
```
<link href="assets/css/Spry/SpryValidation.css" rel="stylesheet" type="text/css"/>
```
**2- Including the JS files:**
```
<script src="assets/js/Spry/jquery3.5.1.min.js" type="text/javascript"></script>
<script src="assets/js/Spry/SpryValidation.js" type="text/javascript"></script>
<script src="assets/js/Spry/SpryValidator.js" type="text/javascript"></script>
```
## Basic Examples:
#### Html
```
<form id="test" action="" method="GET">
    <div class="form-group">
      <label for="name">Name:</label>
      <input type="text" class="form-control" data-spry="username" id="name">
    </div>
    <div class="form-group">
      <label for="password">Password:</label>
      <input type="password" class="form-control" data-spry="password" id="password">
    </div>
    <div class="form-group">
      <label for="confirm">Confirm:</label>
      <input type="password" class="form-control" data-spry="confirm" id="confirm">
    </div>

    <div class="form-group">
      <label for="url">Url:</label>
      <input type="text" class="form-control" data-spry="url" id="url">
    </div>
    <input id="sprySubmit" type="submit" value="submit">
</form>
```
#### Js
```
$("#test").spryValidator({
    username: {
        isRequired: true,
        startAlphaChars: 2
    },
    password: {
        isRequired: true,
        minUpperAlphaChars: 2
    },
    confirm: {
        isRequired: true
    },
    url: {
        hint:  "http://www.example.com"
    },
    errorMessages: {
        startAlphaChars: "Your name must start with 2 letters at least",
        passwordStrength: "The password must contains at least 2 uppercase letters"
    }
})
```
Here is a simple bootstrap form, and every input has a data-spry attribute which represents the type of that input in this case it is (username, password, confirm, and url).
<br>
In the Js section we selected the container with its id and called on it the spryValidator plugin, and passed to the plugin an object as a parameter with the options we need, in this case, all the inputs are required except the url, the username must start with tow letters at least, the password must contain at least two alpha characters, and we customized the errors messages.
<br>
**Note that:** you must add the **data-spry** attribute to any input you want to validate, if you want to prevent spryValidator plugin to interact with an input don't give it a **data-spry** attribute.
<br>
**Note that:** if we want to confirm the password input in another input like the example above, we **must** give the main password input an id.
<br>
**Note that:** if you are validating your inputs by the **HTML** input attributes like (required, min, max, etc.,) the spryValidater plugin will detect it and include them in the validation process.

## The data-spry attribute (Required):

The **data-spry** attribute accepts the following values only: (**none**, **username**, **password**, **confirm**, **integer**, **email**, **date**, **time**, **credit_card**, **zip_code**, **phone_number**, **social_security_number**, **currency**, **real**, **ip**, **url**, **textarea**, **select**, **radio**, **checkbox**, and **custom**).
<br>
**And here is the spryValidator plugin default options object with all the acceptable options, the acceptable values for these options, and the other varieties if exists:**
```
{
 none: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    minChars: null, // Positive integer value
    maxChars: null, // Positive integer value
    hint: null // describes how to fill this field
 },
 username: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    minChars: null, // Positive integer value
    maxChars: null, // Positive integer value
    minAlphaChars: null, // Positive integer value
    maxAlphaChars: null, // Positive integer value
    startAlphaChars: null, // Positive integer value
    hint: null // describes how to fill this field
 },
 integer: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    useCharacterMasking: false, // Boolean
    allowNegative: false, // Boolean
    minValue: null, // Integer value
    maxValue: null, // Integer value
    hint: null // describes how to fill this field
 },
 email: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    minChars: null, // Positive integer value
    maxChars: null, // Positive integer value
    hint: null // describes how to fill this field
 },
 date: {
    format: "dd/mm/yyyy", // (other varieties): "mm/dd/yyyy"; "dd/mm/yy"; "yy/mm/dd"; "yyyy/mm/dd"; "mm-dd-yy"; "dd-mm-yy"; "yyyy-mm-dd"; "mm.dd.yyyy"; "dd.mm.yyyy"; "mm/dd/yy";
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    useCharacterMasking: true, // Boolean (recommended)
    minValue: null, // Date value in the specified format
    maxValue: null, // Date value in the specified format
    hint: "dd/mm/yyyy" // describes how to fill this field (recommended)
 },
 time: {
    format: "HH:mm", // (other varieties): "HH:mm:ss"; "hh:mm tt"; "hh:mm:ss tt"; "hh:mm t"; "hh:mm;ss t"; (where "tt" stands for am/pm format, and "t" stands for a/p format.)
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: true, // Boolean
    useCharacterMasking: false, // Boolean (recommended)
    minValue: null, // Time value in the specified format
    maxValue: null, // Time value in the specified format
    hint: "HH:mm" // describes how to fill this field (recommended)
 },
 credit_card: {
    format: null, // (other varieties): "visa"; "mastercard"; "amex"; "discover"; "dinersclub" (recommended)
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    useCharacterMasking: true, // Boolean (recommended)
    minChars: null, // Positive integer value
    maxChars: null, // Positive integer value
    hint: null // describes how to fill this field (recommended)
 },
 zip_code: {
    format: "zip_custom", // (other varieties): "zip_us9"; "zip_custom"; "zip_canada"; "zip_us5"; "zip_uk" ("zip_custom" is recommended)
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    useCharacterMasking: true, // Boolean (recommended)
    minChars: null, // Positive integer value
    maxChars: null, // Positive integer value
    pattern: null, // Custom zip code pattern. Used when format="zip_custom" (recommended)
    hint: null // describes how to fill this field (recommended)
 },
 phone_number: {
    format: 'phone_custom', // (other varieties): "phone_number"; ('phone_custom' is recommended)
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    useCharacterMasking: true, // Boolean (recommended)
    minChars: null, // Positive integer value
    maxChars: null, // Positive integer value
    pattern: null, // Custom phone pattern. (recommended)
    hint: null // describes how to fill this field (recommended)

 },
 social_security_number: {
    format: "custom",
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    useCharacterMasking: true, // Boolean (recommended)
    minChars: null, // Positive integer value
    maxChars: null, // Positive integer value
    pattern: null, // Custom social security pattern (recommended)
    hint: null // describes how to fill this field (recommended)
 },
 currency: {
    format: "comma_dot", // (other varieties): "dot_comma"
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    useCharacterMasking: true, // Boolean
    minValue: null, // Numeric value with two decimal numbers allowed
    maxValue: null, // Numeric value with two decimal numbers allowed
 },
 real: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    useCharacterMasking: true, // Boolean
    minValue: null, // Numeric value with decimal numbers
    maxValue: null // Numeric value with decimal numbers
 },
 ip: {
    format: "ipv4_ipv6", // (other varieties): "ipv6"; "ipv4"
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    useCharacterMasking: true, // Boolean
 },
 url: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    minChars: null, // Positive integer value
    maxChars: null, // Positive integer value
    hint: null // optional
 },
 checkbox: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    minSelections: null, // Can be modefid by positive integer value
    maxSelections: null // Can be modefid by positive integer value
 },
 radio: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false // Boolean
 },
 select: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    invalidValue: null // accepts a value of an option
 },
 password: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    minChars: "none", // The minimum number of characters required for a valid password.
    maxChars: "none", // The maximum allowable length of the password.
    minAlphaChars: "none", // Minimum number of letters required for a password to be valid.
    maxAlphaChars: "none", // Maximum number of letters required for a password to be valid.
    minUpperAlphaChars: "none", // Minimum number of upper case letters required for a password to be valid.
    maxUpperAlphaChars: "none", // Maximum number of upper case letters required for a password to be valid.
    minSpecialChars: "none", // Minimum number of special characters required for a password to be valid.
    maxSpecialChars: "none", // Maximum number of special characters required for a password to be valid.
    minNumbers: "none", // Minimum number of numbers required for a password to be valid.
    minNumbers: "none" // Maximum number of numbers required for a password to be valid.
 },
 confirm: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false // Boolean
 },
 textarea: {
    validateOn: ['blur', 'change'], // (other varieties): ["blur"]; ["change"]; or both together (["blur", "change"])
    isRequired: false, // Boolean
    useCharacterMasking: false, // Boolean
    minChars: null, // Positive integer value
    maxChars: null, // Positive integer value
    counterType: null, // optional... example => "chars_remaining"
    counterId: null, // optional... example => "my_counter_span"
    hint: null // optional
 },
 errorMessages: {
    required: "A value is required",
    invalid: "Invalid value",
    maxValue: "The maximum value exceeded",
    minValue: "The minimum value not met",
    maxChars: "The maximum number of characters exceeded",
    minChars: "The minimum number of characters not met",
    maxAlphaChars: "The maximum number of alpha characters exceeded",
    minAlphaChars: "The minimum number of alpha characters not met",
    startAlphaChars: "Start with more letters", // (it is recommended to modify it to mention how many letters the user has to start with)
    makeSelection: "Please make a selection",
    invalidSelection: "Invalid selection",
    passwordStrength: "The password strength condition not met",
    passwordCustom: "User defined condition not met",
    invalidConfirm: "The values do not match",
    maxSelections: "The maximum selections exceeded",
    minSelections: "The minimum selections not met"
 },
 validMessages: {
    validText: "",
    validPassword: "",
    validConfirm: "",
    validSelect: "",
    validCheckbox: "",
    validRadio: "",
    validTextarea: "",
    validCustom: ""
 }
}
```

### Checkbox and radio:

In the case of these **data-spry** types, we must group the checkbox inputs or the radio inputs in a span container like the next example:
#### Html
```
<form id="test" action="" method="GET">
    <div>
        <span data-spry="checkbox">
            <div class="checkbox">
                <label><input type="checkbox" name="checkbox[]" value="1">Option 1</label>
            </div>
            <div class="checkbox">
                <label><input type="checkbox" name="checkbox[]" value="2">Option 2</label>
            </div>
            <div class="checkbox disabled">
                <label><input type="checkbox" name="checkbox[]" value="3" disabled>Option 3</label>
            </div>
        </span>
    </div>
    <br>
    <div>
        <span data-spry="radio">
            <div class="radio">
                <label><input type="radio" name="optradio" >Option 1</label>
            </div>
            <div class="radio">
                <label><input type="radio" name="optradio">Option 2</label>
            </div>
            <div class="radio disabled">
                <label><input type="radio" name="optradio" disabled>Option 3</label>
            </div>
        </span>
    </div>
    <input id="sprySubmit" type="submit" value="submit">
</form>
```
#### Js
```
$("#test").spryValidator({
    radio: {
        isRequired: true,
    },
    checkbox: {
        isRequired: true,
        maxSelections: 2
    }
})
```
### Select:
#### Html
```
<form id="test" action="" method="GET">
    <div class="form-group">
      <label for="sel1">Select list:</label>

      <select class="form-control" data-type="select" id="sel1">
        <option disabled selected value> -- select an option -- </option>
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
      </select>
    </div>
    <input id="sprySubmit" type="submit" value="submit">
</form>
```
#### Js
```
$("#test").spryValidator({
    select: {
        isRequired: true,
        invalidValue: 3
    }
})
```
**Note that:** we must add a value attribute to every option tag because the spryValidator plugin checks on these values.

## Advanced Examples:

### Custom:
If we want to validate an input in a custom way, we can set the **data-spry** attribute to "custom" and we have to give that input a **unique (data-id) attribute**, and in this case we will pass in a key with that **unique (data-id) attribute** and the value of that key will be the object with the customize validation options like the next example.

#### Html
```
<form id="test" action="" method="GET">
  <div class="form-group">
    <label for="code1">Code 1:</label>
    <input data-id="custom1" type="text" class="form-control" data-spry="custom" id="code1">
  </div>
  <div class="form-group">
    <label for="code2">Code 2:</label>
    <input data-id="custom2" type="text" class="form-control" data-spry="custom" id="code2">
  </div>
  <input id="sprySubmit" type="submit" value="submit">
</form>
```

#### Js
```
$("#test").spryValidator({
    custom1 : {
        useCharacterMasking: true,
        validateOn: ['blur'],
        pattern : "00 0000 AA",
        hint: "12 3456 EG"
    },
    custom2 : {
        useCharacterMasking: true,
        validateOn: ['blur'],
        isRequired: false, // It is true by default
        pattern : "?0 0000 aa",
        hint: "#2 3456 eg"
    },
})
```

**The following table shows a full list of values used for custom patterns.**
| Value | Description |
| ----- | ----------- |
| "0" |	Whole numbers between 0 and 9 |
| "A" |	Uppercase alphabetic characters |
| "a" |	Lowercase alphabetic characters |
| "B"; "b" | Case-insensitive alphabetic characters |
| "X" |	Uppercase alpha-numeric characters |
| "x"	| Lowercase alpha-numeric characters |
| "Y"; "y" | Case-insensitive alpha-numeric characters |
|"?" | Any character |

### The onSuccess() method:
Now, this is the main purpose for making this plugin, some times we want to validate inputs that are not inside a ```form``` tag as a container and use the valid data for ajax requests or some other logic code, and here comes the role of the ```onSuccess()``` method like the next example:
#### Html
```
<div id="test">
    <div class="form-group">
      <label for="name">Car name:</label>
      <input type="text" class="form-control" data-spry="none" id="name">
    </div>
    <div class="form-group">
      <label for="model">Model:</label>
      <input type="text" class="form-control" data-spry="none" id="model">
    </div>
    <div class="form-group">
      <label for="phone">Phone:</label>
      <input type="text" class="form-control" data-spry="phone_number" id="phone">
    </div>
    <div class="form-group">
      <label for="Description">Description:</label>
      <textarea class="form-control" data-spry="textarea" rows="4" id="description"></textarea>
      <span id="my_counter_span"></span>
    </div>
    <input id="sprySubmitBtn" type="submit" value="validate">
</div>
```
#### Js
```
$("#test").spryValidator({
    submitBtn: "#sprySubmitBtn",
    none: {
        isRequired: true,
    },
    phone_number: {
        isRequired: true,
        pattern: "(000) 000-00-000",
        hint: "(012) 735-42-801"
     },
    textarea: {
        isRequired: true,
        validateOn: ['blur'],
        minChars: 10,
        maxChars: 200,
        counterType: "chars_remaining",
        counterId: "my_counter_span",
        hint: "Your message!"
    },
    onSuccess: function () {
        console.log("All fields have passed the validation process!");
        // your code if the validation passed
        
    },
})
```
Here we added a key (**submitBtn**) and the value is the id of the button (as a string with # before it) that we want to link with the validation process, when the user click on that button the plugin will check if all the inputs passed the validation, if yes then your code in the ```onSuccess()``` method will be performed.
<br>
**Note that:** you can use the onSuccess method with the ```form``` tag as a container of your inputs to perform some logic code before submitting the form (in this case the **submitBtn** key will not be necessary).
## More Information:
For more information about adobe spry validation open source, you can visit these links:
- [textfield](https://opensource.adobe.com/Spry/articles/textfield_overview/index.html)
- [radio](https://opensource.adobe.com/Spry/articles/radio_overview/index.html)
- [password](https://opensource.adobe.com/Spry/articles/password_overview/index.)
- [confirm](https://opensource.adobe.com/Spry/articles/confirm_overview/index.html)
- [textarea](https://opensource.adobe.com/Spry/articles/textarea_overview/index.html)
- [select](https://opensource.adobe.com/Spry/articles/select_overview/index.html)
- [checkbox](https://opensource.adobe.com/Spry/articles/checkbox_overview/index.html)
