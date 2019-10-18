# Area Directory Mobile Application API Document

<hr>

# BASE URL ‑ https://arcbrain.in/mihu/

<hr>

## Get Offers
* ### Offers List
### API URL : offers/offersApi/get

@Description : This API helps you to view all the offers.
<br>
@Request Type : Post
<br>
@Parameters
  * **Limit** - Integer - (Maximum number of items to be returned in result set. Default is 10)
  * **Page** - Integer - (Current page of the collection. Default is 0)<br>
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
