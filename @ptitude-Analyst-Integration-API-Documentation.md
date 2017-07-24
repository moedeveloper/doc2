# This Section Describe the APIs implemeted in Entreprise Service Bus Integration application.

This application was implemented as a general solution to interact between SKF @A and Maximo platform. This REST application  has returns of JSON format and secured with "TransportCredentialOnly" with the following Credentials:
- username: skf
- password:moemo (please see Section Devops Guide for information about changing username and password)

# APIs

## R1 - Route Childrens/Points

| URL | Parameters |Return|  
|-----------|:-----------:|-----------
| aptitude/childrens | timeStamp | list of object PointIdentity  wrapped   with its route Id; Ids of points in both normal and alarm state |  

The `timeStamp` parameter is the time for the latest uploaded or synchronized data into @A. This parameter is found in ROUTEHDR table (LASTUPLOAD attribute).

A list of `PointsGroup` object which is composed from a list of object `PointIdentity` and its `RouteId` are returned.


![image.png](.attachments/image-bd5e9cb0-43a4-4769-b738-02f7a3aec49b.png)  ![image.png](.attachments/image-d4bf0e5e-ae23-42e1-a890-cb041a74ee47.png)
_Figure 1 get route points_

## R2 - Route Assets/Machine


| URL | Parameters |Return|  
|-----------|:-----------:|-----------
| aptitude/assets| timeStamp | list of object AssetIdentity wrapped with its route Id; Ids of assets in both normal and alarm state |  

timeStamp: same as previous.

A list of `AssetsGroup` object which is composed from a list of object `AssetIdentity` and its `RouteId` are returned.

![image.png](.attachments/image-d2607843-e81f-4cee-b04d-720fa114c3ac.png)  ![image.png](.attachments/image-e812295f-eb1b-4695-a3d7-d59448272760.png)
_Figure 2 get route assets_

## R3 - Route Assets In Alarm

| URL | Parameters |Return|  
|-----------|:-----------:|-----------
| aptitude/assets-in-alarms| timeStamp | list of object AlarmIdentity wrapped with its route Id; Ids of assets in alarm state |  

timeStamp: same as previous.
A list of `RouteAlarm` object which is composed from a list of object `Alarm` and its `RouteId` are returned.

![image.png](.attachments/image-d4fa9628-0663-4e3b-a388-61d6cbe7de53.png)  ![image.png](.attachments/image-2151dd2e-2271-41d4-95d1-9f5023a207d4.png)
_Figure 3 get route assets in alarm state_

## R4 - Route Childrens In Alarm
| URL | Parameters |Return|  
|-----------|:-----------:|-----------
| aptitude/points-in-alarms| timeStamp | list of object AlarmIdentity wrapped with its route Id; Ids of points in alarm state |  

timeStamp: same as previous.
A list of `RouteAlarm` object which is composed from a list of object `Alarm` and its `RouteId` are returned.

**Same object of R3**
![image.png](.attachments/image-a286a91b-31c0-4a89-a51f-21b427ca6a8a.png)
_Figure 4 get route points in alarm state_



## R5 - Route Alarm By Asset

| URL | Parameters |Return|  
|-----------|:-----------:|-----------
| aptitude/alarms-by-asset| assetId| list of object AlarmIdentity; Ids of points in alarm state for one Asset |

assetId paramater can be collected from R2 or R3.

![image.png](.attachments/image-3189073c-32e9-4aa6-8c51-c562130f8917.png)
_Figure 5 get alarms in one asset_

## R6 - Asset Details
| URL | Parameters |Return|  
|-----------|:-----------:|-----------
| aptitude/asset| assetId| asset object |

assetId paramater can be collected from R2 or R3.

asset object: is composed from propreties shown in figure 6


![image.png](.attachments/image-a28e55be-a7f6-4239-a3b1-528dcccf97c5.png)  ![image.png](.attachments/image-bebccbd1-8f65-47d1-869d-e58f8233a531.png)  ![image.png](.attachments/image-0c119d41-f6b5-428d-bb5e-621c16d8cbac.png)
_Figure 6 Asset Information_

Please Note: `ParentId` is one step up in the tree. Also, `HierarchyId` is the Id of the element in the main Hierarchy (the `AssetId` in the route is not the same as the one in the main hierarchy). The `HierarchyId` is used later on to get asset tracking information.

## Point Details

## Message
## Note
## Segmenat and Asset tracking
## Latest Measurement
## Measurements
## Measurement Reading
## Measurements Readings
## Measurement Alarm
## Inspection Alarm
## Scalar Alarm
## MCD Alarm
## Measurement By Time Interval
## Hierarchy

# App Architecture 
# Devops Guide
# Installation
# Repo