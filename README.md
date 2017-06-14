# tooltip
A jQuery plugin for modern tooltips supporting dynamic elements and messages.

## Adding it to your project
### 1. Include jQuery in your project
```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
```
### 2. Download tooltip-complete.min.js and include it in your project
```html
<script src="[YOUR-SCRIPTS-DIRECTORY]/tooltip-complete.min.js"></script>
```

## Usage
There are two ways that tooltips can be added to an element:  

Method 1: Using only JavaScript  

Method 2: Using HTML attributes and classes  

---
### Method 1: Using JavaScript
Add your tooltips to elements in $(document).ready.
```javascript
$(document).ready(function(){
  $('#my-element').tooltip({MY OPTIONS});
});
```
#### Method 1 Options
|  Title   | Required / Optional |  Description  |
| -------- | ------------- | ---------------------- |
| text     | Required | The text the tooltip should contain. |
| delay    | Optional | The amount of time to wait before displaying the tooltip when the user moves the mouse onto the element (in ms). Defaults to 0 |
| fadeDuration | Optional | Fade out duration (in ms). Defaults to 250.| 
| fontSize | Optional | The size for the text in the tooltip (defaults to 1.0em). |
| theme    | Optional | The tooltip theme to use ('dark' or 'light'). Dark is a tooltip with a black background and white text while light is one with a white background and dark grey text. Defaults to dark. |
| textColor | Optional | The color the tooltip text should be (this overrides the default text colors associated with the theme option. See theme option for defaults. |
| shadowColor | Optional | The color of the shadow that is cast by the tooltip. Defaults to '#000' | 
| fontFamily | Optional | The font family to use for the text in the tooltip. Defaults to  'Arial, Helvetica, sans-serif'. <br><br>Example<br>fontFamily: "'Roboto-Medium', 'Roboto-Regular', Arial"|

__Example: Adding a tooltip using the default settings:__
```javascript
$(document).ready(function(){
  $('#my-element').tooltip({text: 'This is a tip'});
});
```

__Example: Adding a tooltip that has a custom font-family and appears 400ms after the mouse enters the element:__
```javascript
$(document).ready(function(){
  $('#my-element').tooltip({
    text: 'This is a tip',
    fontSize: '14px',
    theme: 'light',
    fontFamily: "'Roboto-Medium', 'Roboto-Regular', Arial",
    delay: 400
  });
});
```

### Method 1 actions
The following methods can only be used on tooltips that were added using Method 1. 

#### setText - Changing the tooltip text
```javascript
$('#my-element').tooltip('setText', 'This is the new tooltip text');
```
#### autoTip - Automatically displays the tooltip without user interaction
```javascript
$('#my-element').tooltip('autoTip', {MY OPTIONS});
```
##### Auto tip Options
|  Title   | Required / Optional |  Description  |
| -------- | ------------- | ---------------------- |
| displayDuration | Optional | How long the tooltip should be displayed (in ms). Defaults to 5000. |
| fadeOutDuration | Optional | Duration of the fade out (in ms). Defaults to 1000. |
| onShowCallback | Optional | A function to call when the tooltip appears. |
| onHideCallback | Optional | A function to call when the tooltip disappears. |

__Example: Changing the text of a tooltip using setText and then automatically displaying it using autoTip__
```javascript
 $('#social-messages-button').tooltip('setText', 'You have 1 new message');
 $('#social-messages-button').tooltip('autoTip', {
      displayTime: 4000,
      fadeOutDuration: 5000,
      onShowCallback: function(){
        // play notification sound
      }
  });
```

---

### Method 2: Using HTML attributes and classes
Define your global tip settings in $(document).ready
```javascript
$(document).ready(function(){
  ToolTip.init({
      delay: 400,
      fadeDuration: 250,
      fontSize: '1.0em',
      theme: 'light',                   
      textColor: '#757575',
      shadowColor: '#000',
      fontFamily: "'Roboto-Medium', 'Roboto-Regular', Arial"
  });
});
```

Add tooltips to your HTML markup by adding the __tip-hotspot__ class and __data-tip__ attribute.  
```html
<button class="tip-hotspot" data-tip="This is the tooltip text">Button text here</button>
```
