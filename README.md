<img width="220" src="https://storage.googleapis.com/dx-cdn-public/dx-shared/browser-scripts/brandl-mobility-app-loader/v1/assets/brandl-logo.svg">

<img align="right" width="220" src="https://storage.googleapis.com/dx-cdn-public/dx-shared/browser-scripts/brandl-mobility-app-loader/v1/assets/screenshot.png">Add a Brandl Mobility credit app to any site using the javascript loader. Simply copy a few lines into your site and that's it. The module is less than 2kb gzipped minified and has zero dependencies. 

**Requires that your site is listed at brandlmobility.com.** If you're not already listed at [brandlmobility.com](https://www.brandlmobility.com), contact us and see about getting your mobility dealership listed. No additional security measures within your own site are required.

### Next Step
Share this page with your webmaster. Below are the technical installation and usage instructions.

-----

<br><br>

# Installation

Everything you need is hosted on a CDN and may be used as shown. Use of the CDN hosted script recommended to ensure our changes get reflected at your site.

### Step 1
Decide where the links/buttons should appear on your site and add standard HTML links. Often this is on a single vehicle for sale page, somewhere near the vehicle price. 

IE:
```html
<a href="/whatever/im/replaced" class="my-app-selector">Apply For A Loan</a>
```
The link can be anything you like. Feel free to wrap images, containers or other elements in an **&lt;a&gt;**. While elements such as div, span, img, etc; will work directly, some browsers may block the clicks.  So just wrap whatever in a standard link or button tag.

-----
### Step 2
Place the following script loader on any page containing links/buttons for the financing application.  *You may place this in an include file such as your footer, allowing use on any page of your site.*
```html
<script src="https://storage.googleapis.com/dx-cdn-public/dx-shared/browser-scripts/brandl-mobility-app-loader/v1/bundle.min.js"></script>

<!-- Initialize a basic loader on any page where links/buttons to the application are 
     desired.  The following should be anywhere AFTER the script loader. -->
<script type="application/javascript">
var basicExample = new BrandlAppLoader({  
   selector: 'a.my-app-selector' 
});
</script>

```

In our basic example, submissions include the dealer information and ensures correct assignment.  Optionally, you may include vehicle information. Continue reading to learn how.

-----
### Step 3
Verify things are working by loading a page in your browser and clicking one of your links.  It should open a window with the application.  The dealer's name should be listed in the header directly under "Brandl obility Application".

### What Next
You can include a <a href="#parameter-vehicle"><code>vehicle</code></a> `object` in the <a href="#parameter-initializer"><code>initializer</code></a> parameter or add/update vehicle information via the <a href="#method-setVehicle">setVehicle()</a> method. 


<br><br>
# Debug
If things are not working correctly, see the javascript console as errors will be displayed to help solve the issue. In Google Chrome, right click the page and choose 'Inspect'.




<br><br>
# Demos
Take a look at a few common use working examples.
<ul>
     <li><a href="https://storage.googleapis.com/dx-cdn-public/dx-shared/browser-scripts/brandl-mobility-app-loader/v1/examples/1_basic.html" target="_blank">Basic without vehicle</a></li>
     <li><a href="https://storage.googleapis.com/dx-cdn-public/dx-shared/browser-scripts/brandl-mobility-app-loader/v1/examples/2_include-vehicle.html" target="_blank">Include vehicle data</a></li>
     <li><a href="https://storage.googleapis.com/dx-cdn-public/dx-shared/browser-scripts/brandl-mobility-app-loader/v1/examples/3_add-vehicle.html" target="_blank">Update vehicle using setVehicle()</a></li>
</ul>




<br><br>

# API Reference

## Constructors

### - BrandlAppLoader(<a href="#parameter-initializer">initializer</a>)
@param <a href="#parameter-initializer"><code>initializer</code></a><br>
Used to initialize the loader.  Make sure you call it using 'new'
```javascript 
// Usage
var myRef = new BrandlAppLoader(initializer);
```
<br><br>

## Methods

<a name="method-setVehicle"></a>
### - setVehicle(<a href="#parameter-vehicle">vehicle</a>)
@param <a href="#parameter-vehicle"><code>vehicle</code></a><br>
Add or update the vehicle associated with application. This is useful if your site's page does not reload between vehicle views. The <a href="#parameter-vehicle"><code>vehicle</code></a> object may also be passed in the <a href="#parameter-initializer">`initializer`</a> object.
```javascript 
// Usage
myRef.setVehicle(vehicle);
```

### - getVehicle()
@returns <a href="#parameter-vehicle"><code>vehicle</code></a><br>
Get the current <a href="#parameter-vehicle"><code>vehicle</code></a> `object`. 
```javascript 
// Usage
myRef.getVehicle();
```

### - resetVehicle()
Clear current set vehicle. 
```javascript 
// Usage
myRef.resetVehicle();
```

### - open()
Open the apply window with current settings. If already open, bring to focus. 
```javascript 
// Usage
myRef.open();
```

### - getElements()
@returns list of elements on the page that have been activated. 
```javascript 
// Usage
myRef.getElements();
```



<br><br>

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
      <td valign="top"><code>selector</code></td>
      <td valign="top">string</td>
      <td valign="top"><strong>Required</strong>. The selector to find your elements on the page created in step 1. You might find it best to assign a class to each link/button that is only used for selecting and is separate from styles. All elements matching the provided selector will be modified to open/continue filling out a credit app. Internally, we use <a href="https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll" target="_blank">document.querySelectorAll()</a> to find elements matching provided selector string.</td>
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
    <tr>
      <td valign="top"><code>link</code></td>
      <td valign="top">string</td>
      <td valign="top">A link to the vehicle on your site. Should be the full URL.<br><b>Examples:</b> http://www.your-site.com/path/to/vehicle</td>
    </tr>
  </tbody>
</table>



