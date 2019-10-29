<img src="https://storage.googleapis.com/dx-cdn-public/dx-shared/browser-scripts/brandl-mobility-app-loader/assets/brandl-logo.svg" width="200">


Add a Brandl Mobility credit app to any site using the javascript loader. Simply copy a few lines into your site and that's it. The module is less than 2kb gzipped minified and has zero dependencies. 

**Requires you provide the dealerID obtained from Brandl Mobility.** Not listed at [brandlmobility.com](https://www.brandlmobility.com) yet? Contact us and see about getting your mobility dealership listed. No additional security measures within your own site is required.

### Next Step
Share this page with your webmaster, below are the technical installation and usage instructions.

Installation
------------
Everything you need is hosted on a CDN and may be used as shown. It's recommended to used the CDN hosted files as updates can be made without updated your site.

-----
**Step 1**
Decide where the links/buttons should appear on your site and add standard HTML links. Often this is on a single vehicle for sale page, somewhere near the vehicle price.  For Example: 

**Price: $45,900** -  [Apply Online](https://www.brandlmobility.com)

IE:
```html
<a href="/whatever/im/replaced" class="my-app-selector">Apply Online</a>
```
The link can be anything you like. Feel free to wrap images, containers or other elements in an **&lt;a&gt;**. While elements such as div, span, img, etc; will work directly, some browsers may block the clicks.  So just wrap whatever in a standard link or button tag.

-----
**Step 2**
Place the following script loader on any page links should be upgraded.  *You may place this within an include file such as your footer allowing use on any page of your site.*
```html
<script src="https://dx-cdn-public.storage.googleapis.com/dx-shared/browser-scripts/brandl-mobility-app-loader/dist/bundle.min.gz.js" type="application/javascript"></script>
```
-----
**Step 3**
Initialize the loader on any page where links/buttons to the application are desired.  The following should anywhere AFTER the script load from step 2.

```javascript
var basicExample = new BrandlAppLoader({  
   dealerID: 'Your dealerID Here',  
   selector: 'a.my-app-selector' 
});
```

 - **dealerID**  `string` `required` 
[See below](#locateDealerID) on obtaining the dealerID

 - **selector**  `string` `required` 
Use whatever you like... The selector is used to find the links/buttons created in step 1. You might find it best to assign a class to each link/button that is only used for selecting and separate from styles. All elements matching the provided selector will be modified to open/continue filling out a credit app. Internally, we use [document.querySelectorAll()](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll) to find targeted elements.

D. When you install node.js, will also be installed [npm] (https://www.npmjs.com/).

3. Please run the following command.

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


