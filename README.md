# Area Directory Mobile Application API Document
# BASE URL ‑ https://arcbrain.in/mihu/

## Get Offers
* ### Offers List
### API URL : offers/offersApi/get

@Description : This API helps you to view all the offers.
<br>
@Request Type : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **limit** : Integer | Optional | (Maximum number of items to be returned in result set. Default is 10)
  * **page** : Integer | Optional | (Current page of the collection. Default is 0)<br>
 > If you want to get all offers, Then you need to Set **Limit :** 0 and **Page :** 0

### **Response**
 * Case : False
 <pre>
 {
    "succ": false,
    "public_msg": "Error while Processing."
}
</pre>

* Case : True
<pre>
{
    "succ": true,
    "public_msg": "Offer fetched successfully.",
    "res": {
        "offers": [
            {
                "id": "1",
                "image": "http://arcbrain.in/mihu/beagle_assets/img/offers/1.jpg",
                "data": "{\"action\":\"external_link\",\"url\":\"https:\\/\\/www.nexgi.com\\/\",\"id\":0}",
                "offer_data": {
                    "action": "external_link",
                    "url": "https://www.nexgi.com/",
                    "id": 0
                }
            },
            {
                "id": "2",
                "image": "http://arcbrain.in/mihu/beagle_assets/img/offers/1.jpg",
                "data": "{\"action\":\"category_page\",\"url\":\"\",\"id\":1}",
                "offer_data": {
                    "action": "category_page",
                    "url": "",
                    "id": 1
                }
            },
            {
                "id": "3",
                "image": "http://arcbrain.in/mihu/beagle_assets/img/offers/1.jpg",
                "data": "{\"action\":\"shop_page\",\"url\":\"\",\"id\":1}",
                "offer_data": {
                    "action": "shop_page",
                    "url": "",
                    "id": 1
                }
            }
        ],
        "total_offers": 3
    }
}
</pre>

 * ### Single Offer
 ### API URL : offers/offersApi/get/<offer_id>
        e.g. : offers/offersApi/get/2
 @Description : This API helps you to view single offer.
<br>
@Request Type : Post
<br>
@Response Data Type : Json
<br>
@Parameters : Not Required

### **Response**
 * Case : False
 <pre>
 {
    "succ": false,
    "public_msg": "Error while Processing."
}
</pre>

* Case : True
<pre>
{
    "succ": true,
    "public_msg": "Offer fetched successfully.",
    "res": {
        "id": "2",
        "image": "http://arcbrain.in/mihu/beagle_assets/img/offers/1.jpg",
        "data": "{\"action\":\"category_page\",\"url\":\"\",\"id\":1}",
        "offer_data": {
            "action": "category_page",
            "url": "",
            "id": 1
        }
    }
}
</pre>

<hr>

## Get Categories
* ### Categories List
### API URL : categories/categoryApi/get

@Description : This API helps you to view all the categories.
<br>
@Request Type : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **limit** : Integer | Optional | (Maximum number of items to be returned in result set. Default is 10)
  * **page** : Integer | Optional | (Current page of the collection. Default is 0)<br>
 > If you want to get all offers, Then you need to Set **Limit :** 0 and **Page :** 0
  * **status** : Integer | Optional | (Get Enable Categories or Disable Categories. Default is 1 (Enable))
  > **Options :** 1 for Enable and 0 for Disable
  * **required_child** : Integer | Optional | (Get Categories in Parent - Child format send 1. Default is 0) 
  * **parent_id** : Integer | Optional | (Get Child Categories of given parent_id.)
  * **search_string** : String | Optional | (Get by category name.)
  * **required_featured** : Integer | Optional | (Get featured categories send 1.)
  
### **Response**
 * Case : False
 <pre>
 {
    "succ": false,
    "public_msg": "Error while Processing."
}
</pre>

* Case : True
<br>
If required_child = 1
<pre>
{
    "succ": true,
    "public_msg": "Category Fetched Successfully.",
    "res": {
        "categories": [
            {
                "id": "2",
                "cat_name": "Fitness",
                "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
                "parent_id": "0",
                "status": "1",
                "is_featured": "0",
                "child_category": []
            },
            {
                "id": "3",
                "cat_name": "Hotel",
                "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
                "parent_id": "0",
                "status": "1",
                "is_featured": "0",
                "child_category": [
                    {
                        "id": "5",
                        "cat_name": "Hotel Sub Category",
                        "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
                        "parent_id": "3",
                        "status": "1",
                        "is_featured": "0",
                        "child_category": []
                    }
                ]
            },
            {
                "id": "4",
                "cat_name": "Healthcare",
                "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
                "parent_id": "0",
                "status": "1",
                "is_featured": "0",
                "child_category": [
                    {
                        "id": "6",
                        "cat_name": "Healthcare Sub Category",
                        "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
                        "parent_id": "4",
                        "status": "1",
                        "is_featured": "0",
                        "child_category": []
                    }
                ]
            }
        ]
    }
}
</pre>
If required_child = 0
<pre>
{
    "succ": true,
    "public_msg": "Category Fetched Successfully.",
    "res": {
        "categories": [
            {
                "id": "1",
                "cat_name": "Education",
                "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
                "parent_id": "0",
                "status": "1",
                "is_featured": "0"
            },
            {
                "id": "2",
                "cat_name": "Fitness",
                "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
                "parent_id": "0",
                "status": "1",
                "is_featured": "0"
            },
            {
                "id": "3",
                "cat_name": "Hotel",
                "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
                "parent_id": "0",
                "status": "1",
                "is_featured": "0"
            }
        ]
    }
}
</pre>

* ### Single Category
 ### API URL : categories/categoryApi/get/<category_id>
        e.g. : categories/categoryApi/get/2
 @Description : This API helps you to view single category.
<br>
@Request Type : Post
<br>
@Response Data Type : Json
<br>
@Parameters 
  * **required_child** - Integer | Optional | (Get Categories in Parent - Child format send 1. Default is 0)
  
### **Response**
 * Case : False
 <pre>
 {
    "succ": false,
    "public_msg": "Error while Processing."
}
</pre>

* Case : True
<pre>
<br>
If required_child = 1
{
    "succ": true,
    "public_msg": "Category Fetched Successfully.",
    "res": {
            "id": "3",
            "cat_name": "Hotel",
            "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
            "parent_id": "0",
            "status": "1",
            "is_featured": "0",
            "child_category": [
                {
                    "id": "5",
                    "cat_name": "Hotel Sub Category",
                    "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
                    "parent_id": "3",
                    "status": "1",
                    "is_featured": "0",
                    "child_category": []
                }
            ]
    }
}
</pre>

If required_child = 0
<pre>
{
    "succ": true,
    "public_msg": "Category Fetched Successfully.",
    "res": {
            "id": "2",
            "cat_name": "Fitness",
            "cat_image": "https://arcbrain.in/mihu/beagle_assets/img/categories/Group%202129.svg",
            "parent_id": "0",
            "status": "1",
            "is_featured": "0"
    }
}
</pre>
