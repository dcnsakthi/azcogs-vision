# Animal/Object Detection (Azure Cognitive Services - Computer and Custom Vision APIs)

## Computer Vision API
The Computer Vision API provides state-of-the-art algorithms to process images and return information. For example, it can be used to determine if an image contains mature content, or it can be used to find all the faces in an image. It also has other features like estimating dominant and accent colors, categorizing the content of images, and describing an image with complete English sentences. Additionally, it can also intelligently generate images thumbnails for displaying large images effectively.<br>

<a href="https://southeastasia.dev.cognitive.microsoft.com/docs/services/computer-vision-v3-2/operations/56f91f2e778daf14a499f21b">Cognitive Services APIs Reference (microsoft.com)</a>

 - <u>Step1</u>: Get the API Key and endpoint to authenticate your applications and start sending calls to the service
 - <u>Step2</u>: Try the service in the API console - requires an API Key and selecting your location
 - <u>Step3</u>: Make a web API call - requires your API Key and endpoint
## Custom Vision API
Customize and embed state-of-the-art computer vision image analysis for specific domains with Custom Vision, part of Azure Cognitive Services. Build frictionless customer experiences, optimize manufacturing processes, accelerate digital marketing campaigns, and more. No machine learning expertise is required. <br>

<a href="https://southcentralus.dev.cognitive.microsoft.com/docs/services/Custom_Vision_Training_3.3/operations/5eb0bcc6548b571998fddebd">Cognitive Services APIs Reference (microsoft.com)</a>
 - <u>Step1</u>: In the Endpoint text box, enter the resource endpoint that you copied from the Azure portal.
 - <u>Step2</u>: In the Ocp-Apim-Subscription-Key text box, enter the key that you copied from the Azure portal. If the call requires any more headers, add those with the appropriate values as well.
 - <u>Step3</u>: Provide other parameters, headers, and message payload (body) as required for the operation and select Run.

<img src=".images\CustomVision.jpg" height=450 width=750 border=1>

## Reports & Dashboard
<img src=".images\AnimalDetection.jpg" height=450 width=750 border=1>

<img src=".images\AnimalDetectionSelectted.jpg" height=450 width=750 border=1>
 
## Workflow/Architecture

<img src=".images\Architecture.jpg" height=450 width=750 border=1>

## Services

The below listed services used for this use case.
-	Azure Storage (Input & Output)
-	Azure Computer Vision (Detection)
-	Azure Custom Vision (Detection)
-	Azure Logic App (Orchestration)
-	Azure Cosmos DB (Hot Storage)
-	Microsoft Power BI (Visualization)
 
## Sample Image (Input)
The public image for Azure Cognitive Service Computer & Custom Vision use case.

<img src=".images\InputSource.jpg" height=650 width=750 border=1>

## Sample Result (Output)
Sample Azure Cognitive Service Computer & Custom Vision result for the above public image (without any enhancements).

```
Computer Vision Output:

{
    "id": "062a1990-7bc9-4f72-9be3-a8dadfca3fba",
    "apiVision": "computer",
    "date": "20220108",
    "name": "image9.jpg",
    "path": "/media/wildlife/image9.jpg",
    "objects": [
        {
            "rectangle": {
                "x": 81,
                "y": 244,
                "w": 1043,
                "h": 910
            },
            "object": "African crocodile",
            "confidence": 0.851,
            "parent": {
                "object": "crocodile",
                "confidence": 0.851,
                "parent": {
                    "object": "reptile",
                    "confidence": 0.878,
                    "parent": {
                        "object": "animal",
                        "confidence": 0.911
                    }
                }
            }
        }
    ],
    "_rid": "KdhZAL0BXmhFAAAAAAAAAA==",
    "_self": "dbs/KdhZAA==/colls/KdhZAL0BXmg=/docs/KdhZAL0BXmhFAAAAAAAAAA==/",
    "_etag": "\"d80083c1-0000-1900-0000-61d996910000\"",
    "_attachments": "attachments/",
    "_ts": 1641649809
}
```


```
Custom Vision Output:

{
    "id": "edde7d3c-79c8-4b5f-af07-82beb28949f2",
    "apiVision": "custom",
    "date": "20220108",
    "name": "image9.jpg",
    "path": "/media/wildlife/image9.jpg",
    "objects": [
        {
            "probability": 0.99631435,
            "tagId": "8e0a3a02-33dc-4898-8498-355ff1f2baca",
            "tagName": "crocodile",
            "boundingBox": {
                "left": 0.08588326,
                "top": 0.1107856,
                "width": 0.84312093,
                "height": 0.530886
            }
        }
    ],
    "_rid": "KdhZAL0BXmhEAAAAAAAAAA==",
    "_self": "dbs/KdhZAA==/colls/KdhZAL0BXmg=/docs/KdhZAL0BXmhEAAAAAAAAAA==/",
    "_etag": "\"d80035c0-0000-1900-0000-61d995cb0000\"",
    "_attachments": "attachments/",
    "_ts": 1641649611
}

```

## Input Storage (Source)
The input files are in different formats from Azure Storage (Data Lake Storage Gen2).

<img src=".images\SourcePath.jpg" height=300 width=750 border=1>

## Output Storage (Target)
The output as JSON file to Azure Storage (Data Lake Storage Gen2). 

<img src=".images\TargetComputer.jpg" height=200 width=750 border=1>
<br>
<img src=".images\TargetCustom.jpg" height=200 width=750 border=1>

## End-to-End Process Flow (Orchestration)
The Logic App is used to orchestrate and loop through the images for animal detection using Azure Cognitive Service – Computer & Custom Vision.

<img src=".images\E2EOrhest.jpg" height=150 width=750 border=1>

- Get the blob content from Azure Storage account and pass to Computer Vision (image content) for Azure Cognitive Service – Computer Vision to detect the animals/objects. Finally, write the API detection result in JSON format to Azure Storage account and Cosmos DB.

- Get the blob content from Azure Storage account and pass to Computer Vision (image content) for Azure Cognitive Service – Custom Vision to detect the animals/objects. Finally, write the API detection result in JSON format to Azure Storage account and Cosmos DB.

<img src=".images\LogicAppVision.jpg" height=450 width=750 border=1> 

## E2E with Custom/Computer Vision and Notification (Action)
The Logic App is used to orchestrate and loop through the images for animal detection using Azure Cognitive Service – Custom/Computer Vision with email notification.

<img src=".images\E2EOrhestAction.jpg" height=450 width=750 border=1>

<img src=".images\EmailComputer.png" height=200 width=750 border=1>
<img src=".images\EmailCustom.png" height=200 width=750 border=1> 

***