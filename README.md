# Area Directory Mobile Application API Document
# BASE URL ‑ https://arcbrain.in/mihu/

## Get Location
* ### Search Location
### API URL : location/locationApi/searchLocations

@Description : This API helps you to show location suggestions.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **search** : String | Required | (Search string for get related location suggestions.)
  
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
    "res": [
        {
            "location_name": "Rohini, New Delhi, Delhi, India",
            "place_id": "ChIJPYChRzoBDTkRL16Bd8SM--0"
        },
        {
            "location_name": "Rohini Sector 13, Sector 13, Rohini, Delhi, India",
            "place_id": "ChIJdV8WCmkBDTkRjQ75C5vx9UI"
        },
        {
            "location_name": "Rohini Sector 8 Road, Sector 8, Rohini, Delhi, India",
            "place_id": "EjRSb2hpbmkgU2VjdG9yIDggUm9hZCwgU2VjdG9yIDgsIFJvaGluaSwgRGVsaGksIEluZGlhIi4qLAoUChIJ0yHXGuEDDTkRwBpruEgjnMQSFAoSCaPMTVDgAw05EXc2LM2JyhNL"
        },
        {
            "location_name": "Rohini, West Bengal, India",
            "place_id": "ChIJc7UTAVYSHToRA-RWWRJnwvE"
        },
        {
            "location_name": "Rohini, Jharkhand, India",
            "place_id": "ChIJPacaIho-8TkRumG25AZZPaM"
        }
    ]
}
</pre>

* ### Location Details
### API URL : location/locationApi/getLocationDetails

@Description : This API helps you to show selected location details.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **place_id** : String | Required | (Place id for get related location details.)
  
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
    "res": {
        "location": {
            "lat": 22.1680227,
            "lng": 87.0998788
        },
        "formatted_address": "Rohini, West Bengal, India",
        "name": "Rohini"
    }
}
</pre>

* ### Get Location Details By Latitude and Longitude
### API URL : location/locationApi/getLocByLatLng

@Description : This API helps you to show location using latitude and longitude.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **latitude** : Float | Required | (Current Latitude.)
  * **longitude** : Float | Required | (Current Longitude.)
  
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
    "res": {
        "location": "Karatal District, Kazakhstan",
        "place_id": "ChIJ-YQY6mx1fEIRh7v__4DTJHM"
    },
    "public_msg": "Fetch location successfully."
}
</pre>
<hr>

## My Profile
* ### Register or Update
### API URL : user/userApi/

@Description : This API helps you to registration or update details.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **name** : String | Required | (Name of Customer)
  * **mobile** : Integer | Required | (Mobile number of Customer)
  * **email** : String | Optional | (Email id of Customer)
  * **token** : String | Optional | (Update details)
  
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
* Case : Update Mobile Number
{
    "succ": true,
    "public_msg": "OTP sent on your mobile number for verification.",
    "res": {
        "otp_ref": "4",
        "verify_otp": 1
    }
}

* Case : Update Email id
{
    "succ": true,
    "public_msg": "A verification link is send on your email id.",
    "res": {
        "verify_email": 1
    }
}
</pre>

* ### Resend OTP
### API URL : user/userApi/reSendOtp
@Description : This API helps you to verify OTP.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **mobile** : Integer | Required | (Mobile for verify user and send OTP)
  
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
    "public_msg": "OTP resend successfully.",
    "res": {
        "otp_ref": "4",
        "verify_otp": 1
    }
}
</pre>

* ### Verify OTP
### API URL : user/userApi/verifyOtp
@Description : This API helps you to verify OTP.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **otp** : Integer | Required | (OTP for verification)
  * **otp_ref** : Integer | Required | (OTP Reference number)
  
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
    "public_msg": "Otp verified successfully.",
    "res": {
        "id": "336",
        "name": "Ashish Kumar Pal",
        "email": "",
        "mobile": "8802742352",
        "token": "6c29db1bc03a1c78528a2aa1a34c3c69"
    }
}
</pre>

<hr>

## Get Offers
* ### Offers List
### API URL : offers/offersApi/get

@Description : This API helps you to view all the offers.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **limit** : Integer | Optional | (Maximum number of items to be returned in result set. Default is 10)
  * **page** : Integer | Optional | (Current page of the collection. Default is 0)<br>
  > If you want to get all offers, Then you need to Set **Limit :** 0 and **Page :** 0
  * **status** : Integer | Optional | (Get Enable Offers or Disable Offers.Default Both)
  > **Options :** 1 for Enable and 0 for Disable.
  * **required_count** : Integer | Optional | (Get total no of results are available according to filters).
  * **order** : String | Optional | (Offers sort attribute ascending or descending. )
  > **Options :** asc and desc. Default is desc.
  * **orderby** : String | Optional | (Sorting Offers.)
  > **Options :** sorting and id. Default is id.

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
@Request Method : Post
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
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **limit** : Integer | Optional | (Maximum number of items to be returned in result set. Default is 10)
  * **page** : Integer | Optional | (Current page of the collection. Default is 0)<br>
 > If you want to get all offers, Then you need to Set **Limit :** 0 and **Page :** 0
  * **status** : Integer | Optional | (Get Enable Categories or Disable Categories. Default Both)
  > **Options :** 1 for Enable and 0 for Disable
  * **required_child** : Integer | Optional | (Get Categories in Parent - Child format send 1. Default is 0) 
  * **parent_id** : Integer | Optional | (Get Child Categories of given parent_id.)
  * **search_string** : String | Optional | (Get by category name.)
  * **required_featured** : Integer | Optional | (Get featured categories send 1.)
  * **order** : String | Optional | (Category sort attribute ascending or descending. )
  > **Options :** asc and desc. Default is desc.
  * **orderby** : String | Optional | (Sorting categories.)
  > **Options :** sorting,cat_name and id. Default is id.
  
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
@Request Method : Post
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

<hr>

## Get Shops
* ### Shops List
### API URL : shop/shopApi/get

@Description : This API helps you to view all the shops.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **latitude** : Float | Required | (Get Nearest shops.)
  * **longitude** : Float | Required | (Get Nearest shops.)
  * **limit** : Integer | Optional | (Maximum number of items to be returned in result set. Default is 10)
  * **page** : Integer | Optional | (Current page of the collection. Default is 0)<br>
  > If you want to get all offers, Then you need to Set **Limit :** 0 and **Page :** 0
  * **status** : Integer | Optional | (Get Enable Shops or Disable Shops. Default Both)
  > **Options :** 1 for Enable and 0 for Disable.
  * **required_images** : Integer | Optional | (Get Images of Shops. Set value 1.)
  * **image_type** : Integer | Optional  | (Get images by type.)
  > **Options :** slider and gallery
  * **required_facilties** : Integer | Optional | (Get Facilities of shops, Set Value 1.)
  * **required_offers** : Integer | Optional | (Get Offers of shops. Set Value 1.)
  * **required_categories** : Integer | Optional | (Get Categories of shops. St Value 1.)
  * **required_reviews** : Integer | Optional | (Get Reviews of shops. Set Value 1.)
  * **required_featured** : Integer | Optional | (Get Featured Shops. Set value 1.)
  * **search_string** : String | Optional | (Get Shops by search.)
  * **required_count** : Integer | Optional | (Get total no of results are available according to filters).
  * **order** : String | Optional | (Offers sort attribute ascending or descending. )
  > **Options :** asc and desc. Default is desc.
  * **orderby** : String | Optional | (Sorting Offers.)
  > **Options :** shop_name and id. Default is id.
  * **category_ids** : Array | Optional | (Filter Shops using category ids).

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
    "public_msg": "Shop Fetched Successfully.",
    "res": {
        "shopes": [
            {
                "id": "1",
                "shop_name": "NexGen Innovators It Services Pvt. Ltd.",
                "featured_image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                "contact_no": "1234567890",
                "whatsapp_no": "1234567890",
                "video_url": "https://www.youtube.com/watch?reload=9&v=3J7vYWFaCoU",
                "shop_desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
                "timing": "10:30 Am - 07:30 Pm",
                "home_service": "0",
                "address": "114B 3rd Floor Sewak Park",
                "pin_code": "110059",
                "locality": "Dwarka Mor",
                "city": "New Delhi",
                "state_id": "963",
                "country_id": "864",
                "latitude": "28.58118100",
                "longitude": "77.05088800",
                "status": "1",
                "is_featured": "0",
                "add_user": "5",
                "add_datetime": "2019-10-18 18:55:17",
                "country": "India",
                "state": "Delhi",
                "images": {
                    "gallery": [
                        {
                            "id": "3",
                            "shop_id": "1",
                            "image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                            "type": "gallery"
                        },
                        {
                            "id": "1",
                            "shop_id": "1",
                            "image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                            "type": "gallery"
                        }
                    ],
                    "slider": [
                        {
                            "id": "4",
                            "shop_id": "1",
                            "image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                            "type": "slider"
                        },
                        {
                            "id": "2",
                            "shop_id": "1",
                            "image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                            "type": "slider"
                        }
                    ]
                },
                "facilities": [
                    {
                        "id": "4",
                        "shop_id": "1",
                        "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry."
                    },
                    {
                        "id": "3",
                        "shop_id": "1",
                        "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry."
                    },
                    {
                        "id": "2",
                        "shop_id": "1",
                        "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry."
                    },
                    {
                        "id": "1",
                        "shop_id": "1",
                        "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry."
                    }
                ],
                "reviews": [
                    {
                        "id": "1",
                        "shop_id": "1",
                        "user_id": "5",
                        "rating_stars": "2",
                        "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                        "add_datetime": "2019-10-23 17:36:32",
                        "first_name": "Anup",
                        "last_name": "kumar",
                        "profile_pic": null
                    }
                ],
                "categories": [
                    {
                        "cat_name": "Fitness",
                        "id": "2"
                    },
                    {
                        "cat_name": "Education",
                        "id": "1"
                    }
                ],
                "offers": [
                    {
                        "id": "1",
                        "offer_title": "Upto 50% off on all tests",
                        "offer_desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                        "shop_id": "1",
                        "shop_name": "NexGen Innovators It Services Pvt. Ltd.",
                        "contact_no": "1234567890",
                        "whatsapp_no": "1234567890",
                        "locality": "Dwarka Mor",
                        "city": "New Delhi",
                        "state": "Delhi",
                        "country": "India"
                    }
                ]
            }
        ],
        "total_shops": 1
    }
}
</pre>

* ### Single Shop
 ### API URL : shop/shopApi/get/<shop_id>
        e.g. : shop/shopApi/get/1
 @Description : This API helps you to view single shop.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters 
  * **required_images** : Integer | Optional | (Get Images of Shops. Set value 1.)
  * **image_type** : Integer | Optional  | (Get images by type.)
  > **Options :** slider and gallery
  * **required_facilties** : Integer | Optional | (Get Facilities of shops, Set Value 1.)
  * **required_offers** : Integer | Optional | (Get Offers of shops. Set Value 1.)
  * **required_categories** : Integer | Optional | (Get Categories of shops. St Value 1.)
  * **required_reviews** : Integer | Optional | (Get Reviews of shops. Set Value 1.)
  
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
    "public_msg": "Shop Fetched Successfully.",
    "res": {
        "id": "1",
        "shop_name": "NexGen Innovators It Services Pvt. Ltd.",
        "featured_image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
        "contact_no": "1234567890",
        "whatsapp_no": "1234567890",
        "video_url": "https://www.youtube.com/watch?reload=9&v=3J7vYWFaCoU",
        "shop_desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
        "timing": "10:30 Am - 07:30 Pm",
        "home_service": "0",
        "address": "114B 3rd Floor Sewak Park",
        "pin_code": "110059",
        "locality": "Dwarka Mor",
        "city": "New Delhi",
        "state_id": "963",
        "country_id": "864",
        "latitude": "28.58118100",
        "longitude": "77.05088800",
        "status": "1",
        "is_featured": "0",
        "add_user": "5",
        "add_datetime": "2019-10-18 18:55:17",
        "country": "India",
        "state": "Delhi",
        "images": {
            "gallery": [
                {
                    "id": "3",
                    "shop_id": "1",
                    "image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                    "type": "gallery"
                },
                {
                    "id": "1",
                    "shop_id": "1",
                    "image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                    "type": "gallery"
                }
            ],
            "slider": [
                {
                    "id": "4",
                    "shop_id": "1",
                    "image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                    "type": "slider"
                },
                {
                    "id": "2",
                    "shop_id": "1",
                    "image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                    "type": "slider"
                }
            ]
        },
        "facilities": [
            {
                "id": "4",
                "shop_id": "1",
                "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry."
            },
            {
                "id": "3",
                "shop_id": "1",
                "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry."
            },
            {
                "id": "2",
                "shop_id": "1",
                "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry."
            },
            {
                "id": "1",
                "shop_id": "1",
                "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry."
            }
        ],
        "reviews": [
            {
                "id": "1",
                "shop_id": "1",
                "user_id": "5",
                "rating_stars": "2",
                "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "add_datetime": "2019-10-23 17:36:32",
                "first_name": "Anup",
                "last_name": "kumar",
                "profile_pic": null
            }
        ],
        "categories": [
            {
                "cat_name": "Fitness",
                "id": "2"
            },
            {
                "cat_name": "Education",
                "id": "1"
            }
        ],
        "offers": [
            {
                "id": "1",
                "offer_title": "Upto 50% off on all tests",
                "offer_desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "shop_id": "1",
                "shop_name": "NexGen Innovators It Services Pvt. Ltd.",
                "contact_no": "1234567890",
                "whatsapp_no": "1234567890",
                "locality": "Dwarka Mor",
                "city": "New Delhi",
                "state": "Delhi",
                "country": "India"
            }
        ]
    }
}
</pre>

<hr>

## Shops Rating
* ### Save Rating
### API URL : shop/shopApi/saveReviews

@Description : This API helps you to save rating of shop.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **token** : | Required | (For Security and verify user.)
  * **shop_id** : Integer | Required | (Id of Shop.)
  * **rating_stars** : Integer | Required | (Rating star of shop by user.)
  > **Options :** 1,2,3,4 and 5. (
                  1 - One Star Rating.
                  2 - Two Star Rating.
                  3 - Three Star Rating.
                  4 - Four Star Rating.
                  5 - Five Star Rating. )
  * **desc** : String | Required | (Description written by user.)
  > Maximum 100 Words are allowed.

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
    "public_msg": "Shop rating successfully."
}
</pre>

* ### Get Shop Reviews
### API URL : shop/shopApi/getShopReviews

@Description : This API helps you to view all the shops reviews.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **shop_id** : Integer | Required | (Shop id.)
  * **limit** : Integer | Optional | (Maximum number of items to be returned in result set. Default is 10)
  * **page** : Integer | Optional | (Current page of the collection. Default is 0)<br>
  > If you want to get all offers, Then you need to Set **Limit :** 0 and **Page :** 0
  * **status** : Integer | Optional | (Get enable shop reviews or disable shop reviews. Default Both)
  > **Options :** 1 for Enable and 0 for Disable.
  * **rating_stars** : Integer | Optionals | (Rating star of shops by user.)
  > **Options :** 1,2,3,4 and 5. (
                  1 - One Star Rating.
                  2 - Two Star Rating.
                  3 - Three Star Rating.
                  4 - Four Star Rating.
                  5 - Five Star Rating. )
  * **required_count** : Integer | Optional | (Get total no of results are available according to filters).
  * **order** : String | Optional | (Offers sort attribute ascending or descending. )
  > **Options :** asc and desc. Default is desc.
  * **orderby** : String | Optional | (Sorting Offers.)
  > **Options :** add_datetime,rating_stars and id. Default is id.

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
    "public_msg": "Reviews fetch successfully",
    "res": {
        "reviews": [
            {
                "id": "5",
                "shop_id": "2",
                "user_id": "12",
                "rating_stars": "5",
                "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "status": "1",
                "add_datetime": "2019-10-24 16:17:33",
                "first_name": "Rajapuri",
                "last_name": "",
                "profile_pic": null
            },
            {
                "id": "4",
                "shop_id": "2",
                "user_id": "5",
                "rating_stars": "2",
                "desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "status": "1",
                "add_datetime": "2019-10-23 17:36:32",
                "first_name": "Anup",
                "last_name": "kumar",
                "profile_pic": null
            }
        ],
        "total_reviews": 2
    }
}
</pre>

<hr>

## Get Star Offers
* ### Star Offers List
### API URL : shop/shopApi/getStarOffers/

@Description : This API helps you to view all the star offers.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **limit** : Integer | Optional | (Maximum number of items to be returned in result set. Default is 10)
  * **page** : Integer | Optional | (Current page of the collection. Default is 0)<br>
  > If you want to get all offers, Then you need to Set **Limit :** 0 and **Page :** 0
  * **status** : Integer | Optional | (Get Enable Offers or Disable Offers.Default Both)
  > **Options :** 1 for Enable and 0 for Disable.
  * **required_count** : Integer | Optional | (Get total no of results are available according to filters).
  * **order** : String | Optional | (Offers sort attribute ascending or descending. )
  > **Options :** asc and desc. Default is desc.
  * **orderby** : String | Optional | (Sorting Offers.)
  > **Options :** offer_title,add_datetime and id. Default is id.
  * **shop_id** : Integer | Optional | (Get Offers of given shop id.)
  * **shop_ids** : Array | Optional | (Get offers of given shop ids.)

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
    "res": {
        "offers": [
            {
                "id": "2",
                "offer_title": "Upto 50% off on all tests",
                "offer_desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "shop_id": "1",
                "shop_name": "NexGen Innovators It Services Pvt. Ltd.",
                "featured_image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                "contact_no": "1234567890",
                "whatsapp_no": "1234567890",
                "locality": "Dwarka Mor",
                "city": "New Delhi",
                "state": "Delhi",
                "country": "India"
            },
            {
                "id": "1",
                "offer_title": "Upto 50% off on all tests",
                "offer_desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "shop_id": "1",
                "shop_name": "NexGen Innovators It Services Pvt. Ltd.",
                "featured_image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
                "contact_no": "1234567890",
                "whatsapp_no": "1234567890",
                "locality": "Dwarka Mor",
                "city": "New Delhi",
                "state": "Delhi",
                "country": "India"
            }
        ],
        "total_offers": 2
    },
    "public_msg": "Star offers get successfully."
}
</pre>

* ### Single Star Offer
 ### API URL : shop/shopApi/getStarOffers/<offer_id>
        e.g. : shop/shopApi/getStarOffers/2
 @Description : This API helps you to view single offer.
<br>
@Request Method : Post
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
    "res": {
        "id": "2",
        "offer_title": "Upto 50% off on all tests",
        "offer_desc": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
        "shop_id": "1",
        "shop_name": "NexGen Innovators It Services Pvt. Ltd.",
        "featured_image": "https://www.nexgi.com/wp-content/uploads/2019/06/nexgi-contact-us-bg-image.png",
        "contact_no": "1234567890",
        "whatsapp_no": "1234567890",
        "locality": "Dwarka Mor",
        "city": "New Delhi",
        "state": "Delhi",
        "country": "India"
    },
    "public_msg": "Star offers get successfully."
}
</pre>
<hr>

## Notification
* ### Save FCM Token
### API URL : notification/notificationApi/saveFcmToken

@Description : This API helps you to save FCM Token and updtae locations of user.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **fcm_token** : String | Required | (Firebase cloud messaging token of device.)
  * **device_ip** : String | Required | (Current device IP.)
  * **current_latitude** : Float | Optional | (Current Location latitude of user.)
  * **current_longitude** : Float | Optional | (Current Location longitude of user.)
  * **selected_latitude** : Float | Optional | (Selected Location latitude of user.)
  * **selected_longitude** : Float | Optional | (Selected Location longitude of user.)
  * **enable_noti** : Integer | Optional | (Manage Enable and disable notification. Default Enable)
  > **Options :** Send 1 For enable notification , Send 0 form disable notification.
  
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
    "public_msg": "Token saved successfully."
}
</pre>
* ### Get Notifications
### API URL : notification/notificationApi/get

@Description : This API helps you to show notification lists..
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **fcm_token** : String | Optional | (Firebase token.)
  * **token** : String | Optional | (Login user token.)
  > **Note :** Any one paramter is required **fcm_token** or **token**.
  * **limit** : Integer | Optional | (Maximum number of items to be returned in result set. Default is 10)
  * **page** : Integer | Optional | (Current page of the collection. Default is 0)<br>
  > If you want to get all offers, Then you need to Set **Limit :** 0 and **Page :** 0
  * **required_count** : Integer | Optional | (Get total no of results are available according to filters).
  * **order** : String | Optional | (Offers sort attribute ascending or descending. )
  > **Options :** asc and desc. Default is desc.
  * **orderby** : String | Optional | (Sorting Notification.)
  > **Options :** noti_title ,add_datetime and id. Default is id.
  
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
    "public_msg": "notification fetched successfully.",
    "res": {
        "notifications": [
            {
                "id": "5",
                "noti_title": "Notification 5",
                "noti_text": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "status": "1",
                "sender_id": "5",
                "created_at": "2019-11-13 23:24:04",
                "read": "0",
                "meta_data": {},
                "ago_time": "1 h"
            },
            {
                "id": "4",
                "noti_title": "Notification 4",
                "noti_text": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "status": "1",
                "sender_id": "5",
                "created_at": "2019-11-13 23:24:04",
                "read": "0",
                "meta_data": {
                    "action": "star_offer_page",
                    "url": "",
                    "id": 1
                },
                "ago_time": "1 h"
            },
            {
                "id": "3",
                "noti_title": "Notification 3",
                "noti_text": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "status": "1",
                "sender_id": "5",
                "created_at": "2019-11-13 23:24:04",
                "read": "0",
                "meta_data": {
                    "action": "shop_page",
                    "url": "",
                    "id": 1
                },
                "ago_time": "1 h"
            },
            {
                "id": "2",
                "noti_title": "Notification 2",
                "noti_text": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "status": "1",
                "sender_id": "5",
                "created_at": "2019-11-13 23:24:04",
                "read": "0",
                "meta_data": {
                    "action": "category_page",
                    "url": "",
                    "id": 1
                },
                "ago_time": "1 h"
            },
            {
                "id": "1",
                "noti_title": "Notification 1",
                "noti_text": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.",
                "status": "1",
                "sender_id": "5",
                "created_at": "2019-11-13 23:24:04",
                "read": "0",
                "meta_data": {
                    "action": "external_link",
                    "url": "https://www.nexgi.com/",
                    "id": 0
                },
                "ago_time": "1 h"
            }
        ],
        "total_notifications": 5
    }
}
</pre>

* ### Mark read notification
### API URL : notification/notificationApi/markRead

@Description : This API helps you to mark read notification.
<br>
@Request Method : Post
<br>
@Response Data Type : Json
<br>
@Parameters
  * **fcm_token** : String | Optional | (Firebase cloud messaging token of device.)
  * **token** : String | Optional | (Login user token.)
  > **Note :** Any one paramter is required **fcm_token** or **token**.
  * **noti_id** : Integer | Required | (Notification id.)
  
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
    "public_msg": "Notification mark read successfully."
}
</pre>
