# CJ Affiliate Universal Tag
CJ Affiliate Universal Tag Template for GTM.

## Overview

<ol>
<li>Create, use, or modify variables
<li>Create, use, or modify Triggers
<li>Create CJ Tags using the CJ Universal Tag Template
<li>Create a Custom HTML Tag with CJ Provided Script
</ol>

## Creating Tags

In order to create CJ tags, please make sure all your variables and triggers are correctly setup, this will make the creation of the tag simpler with less back and forth editing.

<ol>
<li>Login to your GTM Account, click the "Tags" tab and then click "New" button.
<li>Click on "Choose tag type to begin setup..." Click on the search icon and search for "CJ Affiliate - Conversion Tag" from the list of tag options. If you have not used the template previously, you will have to click on

![GTM_UniversalTag_templateGallery](https://user-images.githubusercontent.com/55509975/110401048-b1cfc780-802d-11eb-8fe3-e04cea440824.PNG)
<li>Search for "CJ"

![GTM_UniversalTag_OrderData_Overview](https://user-images.githubusercontent.com/55509975/110400763-14749380-802d-11eb-996f-3f448a8a115f.PNG)
<li>Name your Tag and complete the form.
<ol>
<li>By selecting Order Data this tag will report transactions that occur on your website to CJ.</li>
<li>By selecting Page Data this tag will report data from pages of your site that are not transaction/purchase confirmation pages to CJ.</li>
</ol>

<li>This tag will need to utilize a trigger that will fire the tag on all DOM Ready Events.

<ol>
<li>
Page Data Specific Triggers
<ul><li>Page Data will require an exception to not fire on Confirmation/Order Complete Pages</li></ul>

![GTM_UniversalTag_pageDataTrigger](https://user-images.githubusercontent.com/55509975/110402138-b09f9a00-802f-11eb-9343-4c35a25c42ee.PNG)

![GTM_UniversalTag_PageDataTriggerException](https://user-images.githubusercontent.com/55509975/110529557-40942100-80ce-11eb-800f-e46e631a6dfc.PNG)

</li>
<li>
Order Data Specific Trigger

![GTM_UniversalTag_OrderDataTrigger](https://user-images.githubusercontent.com/55509975/110402400-302d6900-8030-11eb-9eae-bc37c36802fb.PNG)

</li>
</ol>
</ol>

## Create a Custom HTML Tag

<ul>

![GTM_UniversalTag_customHTML](https://user-images.githubusercontent.com/55509975/110536547-70dfbd80-80d6-11eb-9949-7b75bb37a890.PNG)


Advanced Settings need to be updated to fire the Universal Tag before the Custom HTML Tag.


![GTM_UniversalTag_AdvancedSettings](https://user-images.githubusercontent.com/55509975/110550720-071cdf00-80e9-11eb-9134-ca8647d59870.PNG)
</ul>


## Creating Variables

<b>Example Data Layer on the Confirmation Page for reference</b>

```HTML
<script>
window.dataLayer = window.dataLayer || [];
window.dataLayer.push({
'subTotal': '217.9300',
'pageTitle': 'Cart',
'coupon': 'FastandFree',
'discount': '5.95',
'products': [
{
'productTitle': 'Ride 8',
'productType': 'Shoes',
'productBrand': 'Saucony',
'productSku': '635841207280',
'productPrice': '109.9500',
'productQuantity': '1',
'productDiscount': '10'
},
{
'productTitle': 'GEL-DS Trainer® 20',
'productType': 'Shoes',
'productBrand': 'ASICS®',
'productSku': '887749725254',
'productColorId': '361937m',
'productPrice': '87.9900',
'productQuantity': '1',
'productDiscount': '10'
}
]

});
</script>
```
#### Standard Tracking Variables
Create a Data Layer Variable for CJ required (i.e. AMOUNT, ORDERID) and optional values (i.e. COUPON, DISCOUNT) that will need to be dynamic. The Data Layer Variable Name must match what is being passed in the Data Layer on the final confirmation page.

<b>Example Data Layer Variable for AMOUNT</b>

![GTM_AMOUNT_Variable](https://user-images.githubusercontent.com/55509975/110398679-2d7b4580-8029-11eb-9524-90a519b5b93f.JPG)


#### Advanced Tracking Variables
If you would like to track item level data, you will need to create a variable for the array that will house the item values. Create a variable as a Data Layer Variable Type, the Data Layer Variable Name should match the name of the array that contains the item, amount, and quantity objects, in the example below the array name is products.
DataLayer on the Confirmation Page

<b>Example Data Layer Variable for Products Array</b>

![GTM_Products_DataLayerVariable](https://user-images.githubusercontent.com/55509975/110399383-a0d18700-802a-11eb-927c-5255b909c031.JPG)

<b>Example Universal Tag Template Advanced Tracking Settings</b>

This section must be completed if you desire to track item-level information for a purchase or lead. This method allows for product-level reporting and item-level commissioning.

<ul>
<li><b>Products Array</b></li>
<ul>
<li>This value should be a Data Layer Variable that populates your array of Products/Items.</li>
</ul>
<li><b>productSku</b></li>
<ul>
<li>A dataLayer variable is not needed for this field, please input the Object Key for SKU or Product ID within the <i>products</i> array.</li>
</ul>
<li><b>productPrice</b></li>
<ul>
<li>A dataLayer variable is not needed for this field, please input the Object Key for a Products Price within the <i>products</i> array. </li>
</ul>
<li><b>productQuantity</b></li>
<ul>
<li>A dataLayer variable is not needed for this field, please input the Object Key for a Products Quantity within the <i>products</i> array.</li>
</ul>
<li><b>productDiscount</b></li>
<ul>
<li>A dataLayer variable is not needed for this field, please input the Object Key for a Products Discount within the <i>products</i> array.</li>
</ul>
<br/>

![GTM_UniversalTag_Advanced](https://user-images.githubusercontent.com/55509975/110519304-002ea600-80c2-11eb-9a07-1ada0d3adf99.PNG)
</ul>

#### Additional Parameters

Use this section to add any additional name=value pairs needed to be tracked. The drop down menu for Custom Field Names includes all additional fields supported by CJ. Please map the appropriate field value variable to each field name.

<b>Example Universal Tag Template Addtional Parameters Settings</b>

![GTM_UniversalTag_AdditionalParameters](https://user-images.githubusercontent.com/55509975/110533462-df228100-80d2-11eb-97f7-9d1566d22f8a.PNG)


#### Consent Signal

You have an option to enable [Consent Signal](https://developers.cj.com/docs/advertiser-site-tracking/consent-signal-&-loyalty-exemption), which will allow passing of consent status to CJ's tag.

##### Google Consent Mode (recommended)

In case you are using Google Consent Mode compliant consent management platform (CMP), you can select "Google Consent Mode" option and CJ's tag will automatically read consent status. This is the easiest way to enable Consent Signal, as it does not require any additional configuration.

##### Other CMP or Custom Consent Dialog

If non-compliant CMP or custom consent dialog is used, you will need to select "Custom" option and make the consent status available via a variable (values: 1 for consent given, 0 for consent not given). In such a scenario, you will need to trigger the tag with Page Data data type again, on the consent status update event.
