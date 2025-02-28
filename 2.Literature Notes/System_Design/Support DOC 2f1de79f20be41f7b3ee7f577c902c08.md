# Support DOC

---

# General Notes

## Custom Domains

- [Check Available DNS with associated certificates](https://console.cloud.google.com/net-services/loadbalancing/details/http/k8s2-um-uxm5o9iu-default-sllr-dashboard-prod-ld9fan1m?authuser=0&project=bosta-new-infrastructure)
- [Logs to check "add" & "verify" endpoints](https://console.cloud.google.com/logs/query;query=resource.type%3D%22k8s_container%22%0Aresource.labels.project_id%3D%22bosta-new-infrastructure%22%0Aresource.labels.location%3D%22europe-west3%22%0Aresource.labels.cluster_name%3D%22bosta-app-private-cluster-1%22%0Aresource.labels.namespace_name%3D%22default%22%0Alabels.k8s-pod%2Fapp%3D%22sllr-api%22%20severity%3E%3DDEFAULT;cursorTimestamp=2023-08-16T07:34:27.691208126Z;duration=PT5M?authuser=0&project=bosta-new-infrastructure)
- [Check load balancer certificate status](https://console.cloud.google.com/net-services/loadbalancing/advanced/sslCertificates/list?project=bosta-new-infrastructure&authuser=0)
- The [certificate](https://console.cloud.google.com/net-services/loadbalancing/advanced/sslCertificates/details/certificate-iuoqjvrzw?project=bosta-new-infrastructure&authuser=0) for this Sllr business domain failed, we faced this issue before, it happens when the business domain has AAAA record, to fix this the business should:
1. Remove his AAAA record.
2. Delete his domain from custom domains and re-add it.

![Untitled](2.Literature%20Notes/System_Design/Support%20DOC%202f1de79f20be41f7b3ee7f577c902c08/Untitled.png)

![Untitled](2.Literature%20Notes/System_Design/Support%20DOC%202f1de79f20be41f7b3ee7f577c902c08/Untitled%201.png)

## Shopify

Shopify requires orders to be unfulfilled first ⇒ not found

Mark as Paid ≠ No COD ⇒ Payment Gateway is the solution

## Our Calendar

[https://calendar.google.com/calendar/u/0/selfsched?sstoken=UURQYl9tb0prOGFGfGRlZmF1bHR8ZTgwMTQ0MDVkNzc3NzAyOTM3YzhjNDQwMWM1OTJlYTU](https://calendar.google.com/calendar/u/0/selfsched?sstoken=UURQYl9tb0prOGFGfGRlZmF1bHR8ZTgwMTQ0MDVkNzc3NzAyOTM3YzhjNDQwMWM1OTJlYTU)

## Fawry

generates a unique key based on phone number to track COD from stars to Bosta.

### Return Manifest Group Error

Deliveries>return group id maps to a different manifest group

get the correct manifest id from route and assign it to the delivery (search for `RTO_GROUP`)

- Temporary script [until fixed](https://bostateam.atlassian.net/browse/BR-28179)
    
    ```jsx
    // This MongoDB query performs the following tasks:
    // 1. Finds a route with a specific routeId from the routes collection
    // 2. Checks if the route is debriefed, otherwise exits
    // 3. Retrieves all RTO_GROUPS from the route
    // 4. For each RTO_GROUP, retrieves all delivered tracking numbers
    // 5. For each tracking number, sets the returnGroupId to the RTO_GROUP id in the deliveries collection
    
    // Set the routeId variable with the desired routeId
    let routeId = "<routeId>";
    
    // Find the route with the specified routeId from the routes collection
    let route = db.routes.findOne({ _id: routeId });
    
    // Check if the route is debriefed
    if (route && route.state === "Debriefed") {
      // Get all RTO_GROUPS from the route
      let rtoGroups = route.donePoints.filter(
        (donePoint) => donePoint.type === "RTO_GROUP"
      );
    
      // Iterate over each RTO_GROUP
      rtoGroups.forEach((rtoGroup) => {
        // Get all delivered tracking numbers for the current RTO_GROUP
        let trackingNumbers = rtoGroup.deliveredTrackingNumbers;
    
        // Update the manifestId for each tracking number
        db.deliveries.updateMany(
          { trackingNumber: { $in: trackingNumbers } },
          { $set: { returnGroupId: rtoGroup.id } }
        );
      });
    } else {
      console.log("Route is not debriefed.");
    }
    ```
    

 

## API Keys

API Keys has to have same contact number as default user

## Roles

Request that has roles + no admin group ⇒ V0

## Hiding bubble wrap **Re: Issue in bubble warp machine**

hiding country from the item from wallet.flyers in SQL

## Business Dashboard & Admin Dashboard

States are different from each other

## User Permissions

Editor ⇒ cant delete Shipments

Admin ⇒ Full Access

## Emails

Tailing Emails ⇒ Conclusion + Expected Time

## Price plans

need to have pickup location selected first

## Export as XLX

max 50K Entries

### 3PL Creation

1- Create Vendor using Vendor mail and Phone Number

2- Create Admin User (Hub Leader)

3-Create Hub Clerk User 

4-Create Hub and assign Admin User as Hub Leader

5-Add Warehouse info to Admin User

6-Add Vendor object to Hub

### B**ubble orders**

remove Country ID from SQL bubble flyers to hide Bubble from dashboard

pickup up ⇒ requested

### Netsuite Postman Collection

[https://martian-station-294676.postman.co/workspace/Bosta~155992b4-acb5-4064-8a88-8f707ff46366/collection/24090269-37a3f955-2685-4f56-baa9-cf18fed6048b?action=share&creator=24090269](https://martian-station-294676.postman.co/workspace/Bosta~155992b4-acb5-4064-8a88-8f707ff46366/collection/24090269-37a3f955-2685-4f56-baa9-cf18fed6048b?action=share&creator=24090269)

************************************Net-suite Data Sync************************************

```jsx
project field in mongo filter

{bankInfo:1,name:1,admins:1,paymentInfo:1,businessType:1,businessTier:1,businessCategory:1}
```

### Business Document Changing

```jsx
{
  "_id": "qBXo2PzsSayacMhcBAupj",
  "emails": [
    {
      "address": "hamdysara387@gmail.com",
      "verified": true
    }
  ],
  "email": {
    "address": "hamdysara387@gmail.com",
    "verified": true
  },
  "emailToken": null,
  "emailTokenExpiration": null,
  "heardAboutUsFrom": "Tried Bosta as a customer before",
  "isUserFullyActivated": true,
  "isPhoneVerified": true,
  "profile": {
    "firstName": "Sara",
    "lastName": "Hamdy",
    "phone": "+201022157129"
  },
  "roles": [
    "BUSINESS_ADMIN"
  ],
  "businessAdminInfo": {
    "businessId": "asEFFPV0AxAH9nYAMPaLd",
    "businessName": "Zay elgadid"
  },
  "hashedPassword": "$2a$12$NxZNgwgWh2L4/v5ovCs6P.d/LsqyfNeLF1UkNF2nuAwND22h19j7m",
  "group": {
    "_id": "XaqlCFA",
    "name": "BUSINESS_FULL_ACCESS",
    "code": 115
  },
  "state": {
    "code": 20,
    "value": "Active",
    "_id": {
      "$oid": "64c7b847fc5fd6e3b5776554"
    }
  },
  "lastSessionResetDate": {
    "$date": "2023-07-31T13:29:02.255Z"
  },
  "country": {
    "_id": "60e4482c7cb7d4bc4849c4d5",
    "name": "Egypt",
    "nameAr": "مصر",
    "code": "EG"
  },
  "deactivatedAcc": false,
  "regSrc": "DASHBOARD",
  "cities": [],
  "logs": [],
  "createdAt": {
    "$date": "2023-07-31T13:33:59.101Z"
  },
  "updatedAt": {
    "$date": "2023-08-01T07:54:16.067Z"
  },
  "__v": 0,
  "phoneToken": null,
  "tokenExpiration": null,
  "plannedShipmentType": [
    "NORMAL_SHIPMENT"
  ],
  "plannedPricingPlan": "FcsepcvPBk",
  "personalInfoOtp": null,
  "emailUpdateOtp": null,
  "updatedEmailWaitingBusinessVerification": null
}
```

## STAR wallet tracking number not reflected

### deliveries collection

```jsx
{
	"_id": "060010234060", //(same length of string but random)"deliveryId": "NLQ6UqnSWcbMHlCdwu9vr",
"starId": "Bq0Mt8Ie7VpFkmgHkhRuU",
"business": {
"_id": "zs8x1qeMj8IGHrXXZY8Jm",
"name": "Salasa"
},
"amount": 199,
"src": "CCOD", 
"isCollected": false, //***dayman false***
"receiptNo": "0016095509329", //(optional)
"trackingNumber": "57858586",
"hubId": "030000k000s030a", //(star user document)
"countryId": "eF-3f9FZr",  //(star user document)
"createdAt": , 
"updatedAt": ,
"__v": 0
}"createdAt": { //(make sure it’s date format)
"$date": "2018-11-13T09:00:58.862Z"
},
```

## Sign and return flag in db

```python
"type": "B2B"
```

**************************************************************************************Convert a list of puids to state cancelled:**************************************************************************************

```jsx
array=['10285192', '56174636', '58128833', '72543347', '61107238', '13977699', '92722704', '33920064', '45268471', '97242834', '95851737', '65582782', '95423965', '10232562', '48792690', '4058474', '84211044', '29269225', '60918767', '54691398', '22238991', '56338288']
	db.pickupRequests.updateMany({puid:{$in:array}},{$set:{"state":"Canceled"}})
```

****Return OTP endpoint log:****

```
[routeDeliveriesConfirmation][generateRTOConfirmationOTPAndMail]
```

- Add missing SLA to new fulfillment deliveries
    
    ```bash
    var query = {'pickupAddress.country._id': "eF-3f9FZr", type: "FXF_SEND", collectedFromBusiness: {$exists: true}, 'sla.e2eSla': null, isBostaFulfillmentOrder: true};
    var x = db.deliveries.find(query);
    x.forEach(doc => {
        var receivedAtWarehouse = doc.state.receivedAtWarehouse.time.getTime();
        var e2eSlaTimeStamp = new Date(receivedAtWarehouse + 10 * 24 * 60 * 60 * 1000);
        var orderSlaTimeStamp = new Date(receivedAtWarehouse + 2 * 24 * 60 * 60 * 1000);
    
        var sla =  {
            e2eSla: {
                isExceededE2ESla: new Date() > e2eSlaTimeStamp,
                e2eSlaTimestamp: e2eSlaTimeStamp
            },  
            orderSla: {
                isExceededOrderSla: new Date() > orderSlaTimeStamp,
                orderSlaTimestamp: orderSlaTimeStamp
            }
        }
    
        db.deliveries.updateOne({_id: doc._id}, {$set: {"sla": sla}});
    });
    ```
    
- Set CRP pickup requests to picked up by tracking numbers
    
    ```jsx
    var tns = ["5730788", "83012196", "79839415", "..."];
    
    let docs = db.pickupRequests.find({ "deliveries.trackingNumber": { $in: tns } });
    
    docs.forEach(doc => {
      db.pickupRequests.updateOne({ _id: doc._id }, { $set: { "state": "Picked up" } });
    });
    ```
    

### log for SMS

```
[sms/vodafone.js] to [+201003301682] 
```

## Integration removal from a document to add different integration

- Ask the Account manager to cancel the unwanted integration.
- 
- Rename `integrationInfo` field to _
- And then ask the account manger to proceed normally to add the other integration to this shipment

## Fix starInfo outdated after restoring users collection

- Go to debrief star on admin dashboard
- Pick any of the TNs and search for it in DB, get the route ID
- Make sure the star’s user document at `user.starInfo` contains `BUSY` and `routeId` equal to the route ID you found on the TN.

## How to restore a MongoDB collection from GCP

- Coming soon…

## States Mapping

```jsx
Canceled: {
      value: 'DELIVERY_FAILED',
    },
    Terminated: {
      value: 'CANCELLED',
    },
    'Pickup requested': {
      value: 'TICKET_CREATED',
    },
    'Waiting for route': {
      value: 'NOT_YET_SHIPPED',
    },
    'Arrived at business': {
      value: 'AVAILABLE_FOR_PICKUP',
    },
    Delivered: {
      value: 'DELIVERED',
    },
    Fulfilled: {
      value: 'Fulfilled',
    },
    'Returned to stock': {
      value: 'Returned to stock',
    },
    'Delivery confirmed': {
      value: 'DELIVERED',
    },
    Exception: {
      value: 'WAITING_FOR_CUSTOMER_ACTION',
    },
    'En route to warehouse': {
      value: 'IN_TRANSIT',
    },
    'In transit between Hubs': {
      value: 'IN_TRANSIT',
    },
    'Picking up': {
      value: 'AVAILABLE_FOR_PICKUP',
    },
    'Picking up from warehouse': {
      value: 'OUT_FOR_DELIVERY',
    },
    'Arrived at warehouse': {
      value: 'AVAILABLE_FOR_PICKUP',
    },
    'Picked up': {
      value: 'OUT_FOR_DELIVERY',
    },
    Delivering: {
      value: 'OUT_FOR_DELIVERY',
    },
    'Arrived at customer': {
      value: 'RECEIVED_DELIVERY_LOCATION',
    },
    'Route Assigned': {
      value: 'NOT_YET_SHIPPED',
    },
    'Waiting for Pickup': {
      value: 'NOT_YET_SHIPPED',
    },
    'Received at warehouse': {
      value: 'PACKAGE_RECEIVED',
    },
    'Picked up from business': {
      value: 'PACKAGE_RECEIVED',
    },
    'Returned to business': {
      value: 'DELIVERED_TO_SENDER',
    },
    Investigation: {
      value: 'DELAYED',
    },
    Lost: {
      value: 'DELIVERY_FAILED',
    },
    Damaged: {
      value: 'DELIVERY_FAILED',
    },
    'Picking up from consignee': {
      value: 'AVAILABLE_FOR_PICKUP',
    },
    'Picked up from consignee': {
      value: 'PACKAGE_RECEIVED',
    },
    Exchanged: {
      value: 'PACKAGE_RECEIVED',
    }
```

- Torod Webhook logs
    
    [https://console.cloud.google.com/logs/query;query=resource.type%3D"k8s_container"
    resource.labels.project_id%3D"bosta-new-infrastructure"
    resource.labels.location%3D"europe-west3"
    resource.labels.cluster_name%3D"bosta-app-private-cluster-1"
    resource.labels.namespace_name%3D"default"
    labels.k8s-pod%2Fapp%3D"bosta-app" severity>%3D"default"
    -- httpRequest.requestMethod %3D "POST"
    -- "[TorodService][singleStatusWebHook]"
    "http:%2F%2Fapp.bosta.co%2Fapi%2Fv0%2Fintegrations%2Ftorod-order-status"
    -- "78711466"
    -- "REbYU3JUx1flJH0sN0Wo4";summaryFields=:false:32:beginning;cursorTimestamp=2023-12-07T09:06:33.313389530Z;duration=P5D?project=bosta-new-infrastructure](https://console.cloud.google.com/logs/query;query=resource.type%3D%22k8s_container%22%0Aresource.labels.project_id%3D%22bosta-new-infrastructure%22%0Aresource.labels.location%3D%22europe-west3%22%0Aresource.labels.cluster_name%3D%22bosta-app-private-cluster-1%22%0Aresource.labels.namespace_name%3D%22default%22%0Alabels.k8s-pod%2Fapp%3D%22bosta-app%22%20severity%3E%3D%22default%22%0A--%20httpRequest.requestMethod%20%3D%20%22POST%22%0A--%20%22%5BTorodService%5D%5BsingleStatusWebHook%5D%22%0A%22http:%2F%2Fapp.bosta.co%2Fapi%2Fv0%2Fintegrations%2Ftorod-order-status%22%0A--%20%2278711466%22%0A--%20%22REbYU3JUx1flJH0sN0Wo4%22;summaryFields=:false:32:beginning;cursorTimestamp=2023-12-07T09:06:33.313389530Z;duration=P5D?project=bosta-new-infrastructure)
    
- Can't change state from Requested to Picking up state.
    
    Give the user Mark as route assigned for the pick up module
    
- Staging API endpoint
    
    [http://stg-app.bosta.co/api/v2/users/login](http://stg-app.bosta.co/api/v2/users/login)
    
- Log to check for paymob call back
    
    [log](https://console.cloud.google.com/logs/query;query=resource.type%3D%22k8s_container%22%0Aresource.labels.project_id%3D%22bosta-new-infrastructure%22%0Aresource.labels.location%3D%22europe-west3%22%0Aresource.labels.cluster_name%3D%22bosta-app-private-cluster-1%22%0Aresource.labels.namespace_name%3D%22default%22%0Alabels.k8s-pod%2Fapp%3D%22bosta-app%22%20severity%3E%3D%22default%22%0A--%20httpRequest.requestMethod%20%3D%20%22POST%22%0A--%20%22151362951%22%0A--%20jsonPayload.labels.reqId%3D%229LUrgehHZ504RUZV1Gmdw%22%0A--%20timestamp%3D%222023-12-19T12:38:57.447385735Z%22%0A--%20insertId%3D%22yj9v5zbsttl1vc63%22%0A%22http:%2F%2Fapp.bosta.co%2Fapi%2Fv0%2Fpayment%2Fpaymob%2Fcallback%22%0A--%20jsonPayload.req.query.merchant_order_id%3D%22z9NKHRvYmqLgxfXc5ei4Y%22%0A--%20jsonPayload.req.body.obj.order_id%3D%22172341515%22%0A--%20jsonPayload.req.body.obj.order_id%3D%22172164752%22%0AjsonPayload.req.body.obj.order.merchant_order_id%3D%22z9NKHRvYmqLgxfXc5ei4Y%22;summaryFields=:false:32:beginning;cursorTimestamp=2023-12-28T02:48:46.490841802Z;duration=P14D?project=bosta-new-infrastructure)
    
- bostaMaterialFee error fix
    
    The business has been updated to a Pricing tier that is deleted, (deleted field is true in DB), to fix it search for the similar name in Pricing Tier collection, and update the business document with it.
    

# Scripts

# How to run App

```jsx
git clone git@gitlab.com:bosta/app.git
cd app
npm i
```

### Prequesites

make sure to have node version 18+

ensure mongodb is installed and mongod service is running

```jsx
systemctl start mongod
```

ensure redis-server is installed and running

```jsx
systemctl start redis-server
```

### Sequelize setup

```jsx
systemctl start mysql
```

In MySQL Workbench ⇒ Database ⇒ Transfer Wizard

transfer stg_wallets from Staging to Local instance

```jsx
npm start
```

head to ⇒ [http://localhost:3000/health](http://localhost:3000/health) you should be welcomed with an Ok status         

                                       *Congrats on running Bosta App 😆*

### Redis Flush

```jsx
curl --location --request PUT 'https://app.bosta.co/api/v0/utils/redis/flush' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImRON1ppTXFIUWYzcG9Sd1lHIiwicm9sZXMiOlsiU1VQRVJfQURNSU4iXSwiZW1haWwiOiJzaGFkeS5rYW1lbEBib3N0YS5jbyIsImNvdW50cnkiOnsiX2lkIjoiZUYtM2Y5RlpyIiwibmFtZSI6IlNhdWRpIEFyYWJpYSIsIm5hbWVBciI6Itin2YTYs9i52YjYr9mK2KkiLCJjb2RlIjoiU0EifSwicGhvbmUiOiIrMjAxMjc1NTI1MDcwIiwic2Vzc2lvbklkIjoiMUlpRmExMnBuOXF2UVFRNzVGOGFtIiwiaWF0IjoxNjk0OTQwMjI3LCJleHAiOjE2OTYxNDk4Mjd9.IPsCZgWI4KAguTZJiSf_5cw67l0pNltiR4mF9wKSYhM' \
--data '{
    "pattern": "*zoning*"
}'
```

### WooCommerce Commit

```jsx
#Get latest svn code
svn checkout http://plugins.svn.wordpress.org/bosta-woocommerce/
https://plugins.trac.wordpress.org/browser/bosta-woocommerce

#Commit changes
svn add . --force
svn commit -m ""

#Credentials for deployment
User name: bostateam
Pass: g^S4Y9eE.xzQHxh

#Check Changes
https://plugins.trac.wordpress.org/browser/bosta-woocommerce
```

### Force Logout ⇒ for when pickup time not reflecting correctly

```python
curl --location '[https://app.bosta.co/api/v0/users/expireTokens](https://app.bosta.co/api/v0/users/expireTokens)' --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImRON1ppTXFIUWYzcG9Sd1lHIiwicm9sZXMiOlsiU1VQRVJfQURNSU4iXSwiZW1haWwiOiJzaGFkeS5rYW1lbEBib3N0YS5jbyIsImNvdW50cnkiOnsiX2lkIjoiNjBlNDQ4MmM3Y2I3ZDRiYzQ4NDljNGQ1IiwibmFtZSI6IkVneXB0IiwibmFtZUFyIjoi2YXYtdixIiwiY29kZSI6IkVHIn0sInBob25lIjoiKzIwMTI3NTUyNTA3MCIsInNlc3Npb25JZCI6IjQyWEZZckZwVndwdDBiSnJYb3MwUyIsImlhdCI6MTY5MDI4NTk1MywiZXhwIjoxNjkxNDk1NTUzfQ.LonRjyTy5eiEruLQTpFqNtjUh6Y-fUE57BY9oRZqJ-M' --header 'Content-Type: application/json' --data-raw '{"emailList": ["[joudigifts@gmail.com](mailto:joudigifts@gmail.com)"]}'
```

### MongoDB commands and scripts

```python
{$and: [{"sender._id":"bYpH1Ses4YeftrTcLgeEp"},{"creationSrc":"NEW_MASS_UPLOAD"}]}
db.deliveries.distinct("sender._id",{"creationSrc":"NEW_MASS_UPLOAD"})
```

### Push Amazon updates for deliveries

```jsx
curl --location --request POST 'https://as2-api.bosta.co/amazon/status-history' \
	--header 'Content-Type: application/json' \
	--data-raw '{
   	 "trackingNumber":"{TN}"
	}'
```

## Creating MR

```jsx
git pull
git checkout -b "feat/BR-number of the Jira tk/descriptin" 
// click + to files was changed 
git commit -m "feat: description" 
git push // then a new command will appear  take it as copypaste it.
```

## 123456789 Hashed Password

```jsx
$2a$12$NxZNgwgWh2L4/v5ovCs6P.d/LsqyfNeLF1UkNF2nuAwND22h19j7m
```

### Update data in NS

```jsx
curl --location 'https://6184358.restlets.api.netsuite.com/app/site/hosting/restlet.nl?script=54&deploy=1' \ 
--header 'Authorization: OAuth realm="6184358",oauth_consumer_key="35e617363cf0fe2a17a591f4300494926000bcb790229a207426b13cb23f8ab9",oauth_token="72d2b5161a977e34b435b9c0f26c59f022b6ee68234d341a4672d22a3922bba8",oauth_signature_method="HMAC-SHA256",oauth_timestamp="1680167231",oauth_nonce="uERfzmTvQZW",oauth_version="1.0",oauth_signature="U8eLXTWiou5gATTxc6dLPXOgTBaCfRHU%2B%2BQNOF%2BrEc4%3D"' \ --header 'Content-Type: application/json' \
--data '{
   "business": {     "_id": " ",   "paymentFrequency": "Weekly",  "paymentSchedule": [    ]  }}'
```

### Sync Cash out freq. (NS)

[Postman Collection](https://martian-station-294676.postman.co/workspace/Bosta~155992b4-acb5-4064-8a88-8f707ff46366/collection/24090269-37a3f955-2685-4f56-baa9-cf18fed6048b?action=share&creator=24090269)

[Postman](https://martian-station-294676.postman.co/workspace/Bosta~155992b4-acb5-4064-8a88-8f707ff46366/collection/24090269-37a3f955-2685-4f56-baa9-cf18fed6048b?action=share&creator=24090269)

```jsx
curl --location 'https://6184358.restlets.api.netsuite.com/app/site/hosting/restlet.nl?script=54&deploy=1' \
--header 'Authorization: OAuth realm="6184358",oauth_consumer_key="35e617363cf0fe2a17a591f4300494926000bcb790229a207426b13cb23f8ab9",oauth_token="72d2b5161a977e34b435b9c0f26c59f022b6ee68234d341a4672d22a3922bba8",oauth_signature_method="HMAC-SHA256",oauth_timestamp="1679471863",oauth_nonce="SBZgNkgTaPb",oauth_version="1.0",oauth_signature="sF5KvXv0VOdhQ0A%2F6ItF%2FWRKX5sJ6sbr50MOwhvCUwM%3D"' \
--header 'Content-Type: application/json' \
--header 'Cookie: NS_ROUTING_VERSION=LAGGING' \
--data '{
    "business": {
        "_id": "Z8LSuV0IeDvZgVfgCEQij",
        "paymentFrequency": "Weekly",
        "paymentSchedule": [
            "Monday"
        ]
    }
}'
```

## orders not synced in overview page [SQL]

```jsx
select * from wallets.deliveries_dashboard
where delivery_id = "SK1TlhAC9IWiBUYUqqm8o";
```

### *MySQL → MongoDB*

```jsx
UPDATE `wallets`.`deliveries_dashboard` SET `state_code` = '45', `cod_collected_at` = '2023-06-14 10:48:44', `cod_collected_at_timestamp` = '2.003', `delivery_updated_at_timestamp` = '2.003', `total_delivery_time` = '22' WHERE (`id` = '123083286');
```

state_code → state.code

cod_collected_at → state.delivering.time

cod_collected_at_timestamp → 

```python
new Date(state.delivering.time).getTime() / 1000
```

delivery_updated_at_timestamp → 

```python
new Date(state.delivering.time).getTime() / 1000
```

total_delivery_time → (delivery time - picking up time in hours) → 22-24

## Roles

User Group concatinates with V2 Roles

****************Assign Sales Manager to business****************

![Untitled](Untitled%202.png)

![Untitled](Untitled%203.png)

### ***Orders experts google logs from business side:***

`“[DeliveryExporter.js][exportXlsxUsingStreams] + “mail””` 

### GCP salla endpoint

```
resource.type="k8s_container"
resource.labels.project_id="bosta-new-infrastructure"
resource.labels.location="europe-west3"
resource.labels.cluster_name="bosta-app-private-cluster-1"
resource.labels.namespace_name="default"
labels.k8s-pod/app="bosta-app" severity>=DEFAULT
httpRequest.requestUrl="http://app.bosta.co/api/v0/salla/webhook"
jsonPayload.req.body.merchant="827575199"
```

******3PL Integration******

**integrationInfo** object on **********************delieveries********************** collection

```jsx
	/saee-order-status (trackingnumber)
GCP logs 
```

## Bubbles order

The bubble machine is down so we need to disable it. To do so just remove the country_id.

Example:

id 910

![Untitled](Untitled%204.png)

## Simulate order, assign, and change route

1. Create order
2. Create a pickup
3. Add mohaned star to it
4. Create a route
5. From star app login with muhanned  star
6. Get otp’s from databases
7. Mark the order as received from Hub operations
8. 

******************************************************************Update vendor object on delivery****************************************************************** 

```jsx
db.deliveries.updateMany({"trackingNumber":{$in:array}}, {$set:{
"vendor": {
    "_id": "a1valaMKe9i5kkequXhSi",
    "hubId": "030000000029",
    "companyName": "Haram Maxab 3PL",
    "country": {
      "_id": "60e4482c7cb7d4bc4849c4d5",
      "name": "Egypt",
      "nameAr": "مصر",
      "code": "EG"
    }
  }
}})
```

## Create ContractorIn star contractor db add a new document.

- In the starContractor Db add a new document

# To bypass credit limit:

- From db change paymentType to Prepaid (Temp)
- From admin dashboard click edit business and change credit limit to -100,000

### Permission to get remote access of sllr is for TELESALES_SENIOR

- Carriyo endpoints + example log
    - Create Shipment: `POST /api/v0/carriyo/shipments`
    - Shipments History: `/api/v0/carriyo/shipments/history`
    - Generate Label: `/api/v0/carriyo/shipments/:trackingNumber/label`
    - Cancel Shipment: `/api/v0/carriyo/shipments/:trackingNumber/cancel`
    - Schedule Pickup: `/api/v0/carriyo/shipments/:trackingNumber/schedule-collection`
    - [Log](https://console.cloud.google.com/logs/query;cursorTimestamp=2023-10-23T03:28:09.336322550Z;duration=P1D;pinnedLogId=2023-02-01T08:30:23.572775920Z%2Fmknq5amxma0z82df;query=resource.type%3D%22k8s_container%22%0Aresource.labels.project_id%3D%22bosta-new-infrastructure%22%0Aresource.labels.location%3D%22europe-west3%22%0Aresource.labels.cluster_name%3D%22bosta-app-private-cluster-1%22%0Aresource.labels.namespace_name%3D%22default%22%0Alabels.k8s-pod%2Fapp%3D%22bosta-app%22%20severity%3E%3DDEFAULT%0A%22%2Fapi%2Fv0%2Fcarriyo%2Fshipments%22%0A%22505266083%22%0Atimestamp%3D%222023-10-23T03:28:09.336322550Z%22%0AinsertId%3D%22r0e1vrbs3yafsko7%22?project=bosta-new-infrastructure)

### To give access to hub monitors to see this page add the specified hub to the scopes in google user information

![Untitled](Untitled%205.png)

## Request Compensation Departments are displayed from the Collection

```
compensationReasonsConfig
```

## To add a shelf to a hub:

- Go to shelves collection
- Clone a document
- change the hubId to the desired hubId and change the id to a unique id

## Script to create shelves

```jsx
function makeid(length) {
    var result           = '';
    var characters       = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
    var charactersLength = characters.length;
    for ( var i = 0; i < length; i++ ) {
        result += characters.charAt(Math.floor(Math.random() * charactersLength));
    }
    return result;
}

var arr = ["Hold-0", "Hold-1", "Hold-2", "Hold-3", "Hold-4", "Hold-5", "Hold-6", "Hold-7", "Hold-8", "Hold-9", "Scheduled-Saturday", "Scheduled-Sunday", "Scheduled-Monday", "Scheduled-Tuesday", "Scheduled-Wednesday", "Scheduled-Thursday", "Pending- Waiting for Action", "Damage Orders", "Rejection Orders", "Mixed Orders", "Urgent Orders","Archived"]

arr.forEach(el => {
  db.getCollection('shelves').insertOne(
    {
    "_id" : makeid(15),
    "name" : el,
    "hubId" : " hub id",
    "type" : "Normal",
    "createdAt" : ISODate("  "),
    "updatedAt" : ISODate("  ")
})
})
```

## Can’t edit business info error:

- Solve
    - Get the business default pick-up location and insert it in **address** array in business document.

![image (2).png](image_(2).png)