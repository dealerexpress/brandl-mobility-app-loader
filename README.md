<img src="https://storage.googleapis.com/dx-cdn-public/dx-shared/browser-scripts/brandl-mobility-app-loader/assets/brandl-logo.svg" width="200">


Add a Brandl Mobility credit app to any site using the javascript loader. Simply copy a few lines into your site and that's it. The module is less than 2kb gzipped minified and has zero dependencies. 

**Requires you provide the dealerID obtained from Brandl Mobility.** Not listed at [brandlmobility.com](https://www.brandlmobility.com) yet? Contact us and see about getting your mobility dealership listed. No additional security measures within your own site is required.

### Next Step
Share this page with your webmaster, below are the technical installation and usage instructions.

-----

<br><br>

# Installation

Everything you need is hosted on a CDN and may be used as shown. It's recommended to used the CDN hosted files as updates can be made without updated your site.

### Step 1
Decide where the links/buttons should appear on your site and add standard HTML links. Often this is on a single vehicle for sale page, somewhere near the vehicle price.  For Example: 

**Price: $45,900** -  [Apply Online](https://www.brandlmobility.com)

IE:
```html
<a href="/whatever/im/replaced" class="my-app-selector">Apply For A Loan</a>
```
The link can be anything you like. Feel free to wrap images, containers or other elements in an **&lt;a&gt;**. While elements such as div, span, img, etc; will work directly, some browsers may block the clicks.  So just wrap whatever in a standard link or button tag.

-----
### Step 2
Place the following script loader on any page containing links links/buttons for the financing application.  *You may place this in an include file such as your footer allowing use on any page of your site.*
```html
<script src="https://dx-cdn-public.storage.googleapis.com/dx-shared/browser-scripts/brandl-mobility-app-loader/dist/bundle.min.gz.js"></script>

<!-- Initialize a basic loader on any page where links/buttons to the application are 
     desired.  The following should be anywhere AFTER the script loader. -->
<script type="application/javascript">
var basicExample = new BrandlAppLoader({  
   dealerID: 'demo',  
   selector: 'a.my-app-selector' 
});
</script>

```

In our basic example, submitions include the dealer information and ensures correct assignment.  Optionally, you may include vehicle information. Continue reading to learn how.

-----
### Step 3
Verify things are working by loading a page in your browser and clicking one of your links.  It should open a window with the application.  The dealer's name should be listed in the header directly under "Brand Mobility Application".

### What Next
You can include a <a href="#parameter-vehicle"><code>vehicle</code></a> `object` in the <a href="#parameter-initializer"><code>initializer</code></a> parameter or add/update vehicle information via the <a href="#method-vehicleSet">setVehicle()</a> method. 



# Debug
If things are not working correctly, see the javascript console as errors will be displayed to help solve the issue. In Google Chrome, right click the page and choose 'Inspect'.


<br><br>

# API Reference

## Constructors

### - BrandlAppLoader(<a href="#parameter-initializer">initializer</a>)
@param <a href="#parameter-initializer"><code>initializer</code></a><br>
Used to initialize the loader.  Make sure you you call it using 'new'
```javascript 
// Usage
var myRef = new BrandlAppLoader(initializer);
```
---

## Methods
<a name="method-vehicleSet"></a>
### - vehicleSet(<a href="#parameter-vehicle">vehicle</a>)
@param <a href="#parameter-vehicle"><code>vehicle</code></a><br>
Add or update the vehicle associated with application. This is useful if your site's page does not reload between vehicle views. The <a href="#parameter-vehicle"><code>vehicle</code></a> object may also be passed in the <a href="#parameter-initializer">`initializer`</a> object.
```javascript 
// Usage
myRef.vehicleSet(vehicle);
```
<br>

### - vehicleGet()
@returns <a href="#parameter-vehicle"><code>vehicle</code></a><br>
Get the current <a href="#parameter-vehicle"><code>vehicle</code></a> `object`. 
```javascript 
// Usage
myRef.vehicleGet();
```
<br>





<br>

## Parameters

<a name="parameter-initializer"></a>
### {initializer}
Type: `object`
<table>
  <thead>
       <tr>
      <th>Name</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td valign="top"><code>dealerID</code></td>
      <td valign="top">string</td>
      <td valign="top"><strong>Required</strong>. The dealerID for the site your placing this on. <a href="#locateDealerID">See Here</a></td>
    </tr>
    <tr>
      <td valign="top"><code>selector</code></td>
      <td valign="top">string</td>
      <td valign="top"><strong>Required</strong>. The selector to find your elements on the page created in step 1. You might find it best to assign a class to each link/button that is only used for selecting and separate from styles. All elements matching the provided selector will be modified to open/continue filling out a credit app. Internally, we use <a href="https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll" target="_blank">document.querySelectorAll()</a> to find elements matching provided selector string.</td>
    </tr>
    <tr>
      <td valign="top"><a href="#parameter-vehicle"><code>vehicle</code></a></td>
      <td valign="top">object</td>
      <td valign="top">An object with information about the vehicle being applied for. <a href="#parameter-vehicle">See vehicle definition</a></td>
    </tr>
  </tbody>
</table>


<a name="parameter-vehicle"></a>
### {vehicle}
Type: `object`
<table>
  <thead>
     <tr>
       <th>Name</th>
       <th>Type</th>
       <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td valign="top"><code>year</code></td>
      <td valign="top">string,number</td>
      <td valign="top">The model year of the vehicle.<br><b>Example:</b> 2018</td>
    </tr>
    <tr>
      <td valign="top"><code>make</code></td>
      <td valign="top">string</td>
      <td valign="top">The make of the vehicle.<br><b>Example:</b> Dodge</td>
    </tr>
    <tr>
      <td valign="top"><code>model</code></td>
      <td valign="top">string</td>
      <td valign="top">The model of the vehicle. You may also include the vehicle's trim level in this field.<br><b>Example:</b> Grand Caravan SE</td>
    </tr>
    <tr>
      <td valign="top"><code>vin</code></td>
      <td valign="top">string</td>
      <td valign="top">The VIN of the vehicle.<br><b>Example:</b> 2FG3FSD8RSW745869</td>
    </tr>
    <tr>
      <td valign="top"><code>stock</code></td>
      <td valign="top">string</td>
      <td valign="top">The dealer defined Stock Number of the vehicle.<br><b>Example:</b> D4583</td>
    </tr>
    <tr>
      <td valign="top"><code>conversion</code></td>
      <td valign="top">string</td>
      <td valign="top">The mobility conversion for the vehicle.<br><b>Example:</b> VMI Northstar</td>
    </tr>
    <tr>
      <td valign="top"><code>miles</code></td>
      <td valign="top">string,number</td>
      <td valign="top">How many miles are on the vehicle.<br><b>Example:</b> 24,526 or 24526</td>
    </tr>
    <tr>
      <td valign="top"><code>price</code></td>
      <td valign="top">string,number</td>
      <td valign="top">The selling price of the vehicle.<br><b>Examples:</b> $28,526 or $28,526.00 or 28526</td>
    </tr>
  </tbody>
</table>




```
npm install --save string
```

<a name="locateDealerID"></a>
Experiment with String.js Now
-----------------------------

Assuming you're on http://stringjs.com, just simply open up the Webkit inspector in either Chrome or Safari, or the web console in Firefox and you'll notice that `string.js` is included in this page so that you can start experimenting with it right away.



Usage
-----

### Node.js

```javascript
var S = require('string');
```

Originally, I was using `$s` but glancing over the code, it was easy to confuse `$s` for string.js with `$` for jQuery. Feel free to use the most convenient variable for you.


### Rails

Checkout this gem to easily use string.js on the asset pipeline: https://github.com/jesjos/stringjs-rails



### Browsers

```html
<!-- HTML5 -->
<script src="https://cdn.rawgit.com/jprichardson/string.js/master/dist/string.min.js"></script>

<!-- Note that in the mime type for Javascript is now officially 'application/javascript'. If you
set the type to application/javascript in IE browsers, your Javacript will fail. Just don't set a
type via the script tag and set the mime type from your server. Most browsers look at the server mime
type anyway -->

<!-- For HTML4/IE -->
<script type="text/javascript" src="https://cdn.rawgit.com/jprichardson/string.js/master/dist/string.min.js"></script>
```

A global variable `window.S` or simply `S` is created.


### AMD Support

It now [has AMD support](https://github.com/jprichardson/string.js/pull/20). See [require.js](http://requirejs.org/) on how to use with AMD modules.


### Both

```javascript
var doesIt = S('my cool string').left(2).endsWith('y'); //true
```

Access the wrapped string using `s` variable or `toString()`

```javascript
var name = S('Your name is JP').right(2).s; //'JP'
```

is the same as…

```javascript
var name = S('Your name is JP').right(2).toString(); //'JP'
```

Still like the clean look of calling these methods directly on native Strings? No problem. Call `extendPrototype()`. Make sure to not call this at the module level, at it'll effect the entire application lifecycle. You should really only use this at the method level. The one exception being if your application will not be a dependency of another application.

```javascript
S.extendPrototype();
var name = 'Your name is JP'.right(2); //'JP'
S.restorePrototype(); //be a good citizen and clean up
```


### Browser Compatibility

`string.js` has been designed to be compatible with Node.js and with IE6+, Firefox 3+, Safari 2+, Chrome 3+. Please [click here][browsertest] to run the tests in your browser. Report any browser issues here: https://github.com/jprichardson/string.js/issues


### Extending string.js

See: https://github.com/jprichardson/string.js/pull/57



Native JavaScript Methods
-------------------------

`string.js` imports all of the native JavaScript methods. This is for convenience. The only difference is that the imported methods return `string.js` objects instead of native JavaScript strings. The one exception to this is the method `charAt(index)`. This is because `charAt()` only returns a string of length one. This is typically done for comparisons and a `string.js` object will have little to no value here.

All of the native methods support chaining with the `string.js` methods.

**Example:**

```javascript
var S = require('string');

var phrase = S('JavaScript is the best scripting language ever!');
var sub = 'best scripting';
var pos = phrase.indexOf(sub);
console.log(phrase.substr(pos, sub.length).truncate(8)); //best...
```


Methods
-------

See [test file][testfile] for more details.

I use the same nomenclature as Objective-C regarding methods. **+** means `static` or `class` method. **-** means `non-static` or `instance` method.

### - constructor(nativeJsString) ###

This creates a new `string.js` object. The parameter can be anything. The `toString()` method will be called on any objects. Some native objects are used in some functions such as `toCSV()`.

Example:

```javascript
S('hello').s //"hello"
S(['a,b']).s //"a,b"
S({hi: 'jp'}).s //"[object Object]""
```


### - between(left, right)

Extracts a string between `left` and `right` strings.

Example:

```javascript
S('<a>foo</a>').between('<a>', '</a>').s // => 'foo'
S('<a>foo</a></a>').between('<a>', '</a>').s // => 'foo'
S('<a><a>foo</a></a>').between('<a>', '</a>').s // => '<a>foo'
S('<a>foo').between('<a>', '</a>').s // => ''
S('Some strings } are very {weird}, dont you think?').between('{', '}').s // => 'weird'
S('This is a test string').between('test').s // => ' string'
S('This is a test string').between('', 'test').s // => 'This is a '
```

### - camelize()

Remove any underscores or dashes and convert a string into camel casing.

Example:

``javascript
S('data_rate').camelize().s; //'dataRate'
S('background-color').camelize().s; //'backgroundColor'
S('-moz-something').camelize().s; //'MozSomething'
S('_car_speed_').camelize().s; //'CarSpeed'
S('yes_we_can').camelize().s; //'yesWeCan'
```


### - capitalize() ###

Capitalizes the first character of a string.

Example:

```javascript
S('jon').capitalize().s; //'Jon'
S('JP').capitalize().s; //'Jp'
```


### - chompLeft(prefix)

Removes `prefix` from start of string.

Example:

```javascript
S('foobar').chompLeft('foo').s; //'bar'
S('foobar').chompLeft('bar').s; //'foobar'
```


### - chompRight(suffix)

Removes `suffix` from end of string.

Example:

```javascript
S('foobar').chompRight('bar').s; //'foo'
S('foobar').chompRight('foo').s; //'foobar'
```


