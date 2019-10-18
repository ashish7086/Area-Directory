# <center> Area Directory Mobile Application API Document </center>
# BASE URL ‑ https://arcbrain.in/mihu/

* ## Get Offers
### API URL : offers/offersApi/get

@Description : This API helps you to view all the offers.
<br>
@Request Type : Post
<br>
@Parameters
  * **Limit** - Integer - (Maximum number of items to be returned in result set. Default is 10)
  * **Page** - Integer - (Current page of the collection. Default is 0) 

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
    "data": [
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
    ]
}
</pre>
