# CJ Affiliate Universal Tag
CJ Affiliate Universal Tag Template for GTM.

## Overview

<ol>
<li>Create, use, or modify variables
<li>Create, use, or modify Triggers
<li>Create CJ Tags using the CJ Universal Tag Template
</ol>


## Creating Variables

#### Standard Tracking Variables
1. Create a Data Layer Variable for AMOUNT. The Data Layer Variable Name must match what is being passed in the Data Layer on the final confirmation page.

(/CJ-Affiliate-Universal/GTM_Tag_New.PNG)

2. Create Data Layer Variables for coupon, discount, and order id (unless the order id is going to be a random number generated by GTM). The Data Layer Variable Name must match what is being passed in the Data Layer on the final confirmation page.

DataLayer on the Confirmation Page
```
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
Discount Variable within GTM
#### Advanced Tracking Variables
If you would like to track item level data, you will need to create a variable for the array that will house the item values. Create a variable as a Data Layer Variable Type, the Data Layer Variable Name should match the name of the array that contains the item, amount, and quantity objects, in the example below the array name is products.
DataLayer on the Confirmation Page

Products Variable within GTM

## Creating Tags

In order to create a CJ tag, please make sure all your variables and triggers are correctly setup, this will make the creation of the tag simpler with less back and forth editing.

<ol>
<li>Login to your GTM Account, click the "Tags" tab and then click "New" button.
<li>Click on "Choose tag type to begin setup..." Click on the search icon and search for "CJ Affiliate - Conversion Tag" from the list of tag options. If you have not used the template previously, you will have to click on 
<li>Search for "CJ" 
<li>Name your Tag and complete the form.
<li>This tag will need to utilize a trigger that will fire the tag on all pages.
</ol>








