# Animal Detection (Azure Cognitive Services - Computer and Custom Vision APIs)

## Computer Vision API
The Computer Vision API provides state-of-the-art algorithms to process images and return information. For example, it can be used to determine if an image contains mature content, or it can be used to find all the faces in an image. It also has other features like estimating dominant and accent colors, categorizing the content of images, and describing an image with complete English sentences. Additionally, it can also intelligently generate images thumbnails for displaying large images effectively.
Cognitive Services APIs Reference (microsoft.com)
•	Step1: Get the API Key and endpoint to authenticate your applications and start sending calls to the service
•	Step2: Try the service in the API console - requires an API Key and selecting your location
•	Step3: Make a web API call - requires your API Key and endpoint
## Custom Vision API
Customize and embed state-of-the-art computer vision image analysis for specific domains with Custom Vision, part of Azure Cognitive Services. Build frictionless customer experiences, optimize manufacturing processes, accelerate digital marketing campaigns, and more. No machine learning expertise is required. 
Cognitive Services APIs Reference (microsoft.com)
•	Step1: In the Endpoint text box, enter the resource endpoint that you copied from the Azure portal.
•	Step2: In the Ocp-Apim-Subscription-Key text box, enter the key that you copied from the Azure portal. If the call requires any more headers, add those with the appropriate values as well.
•	Step3: Provide other parameters, headers, and message payload (body) as required for the operation and select Run.
## Animal Detection 
 
## Workflow & Services
The below listed services used for this POC.
-	Azure Storage (Input & Output)
-	Azure Computer Vision (Detection)
-	Azure Logic App (Orchestration)
-	Azure Cosmos DB (Hot Storage)
-	Microsoft Power BI (Visualization)
 
## Sample Image (Input)
The public image for a quick Azure Cognitive Service Computer Vision POC.
  
## Sample Result (Output)
Sample Azure Cognitive Service Computer Vision result for the above public image (without any enhancements).
{
	"objects": [{
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
	"requestId": "d3c041fa-9d7b-48ed-b171-2362f9de8759",
	"metadata": {
		"height": 1799,
		"width": 1200,
		"format": "Jpeg"
	}
}
## Input Storage (Source)
The input files are in different formats from Azure Storage.
 
## Output Storage (Target)
The output as JSON file to Azure Storage. 
 
 
## Computer Vision Config (Logic App)
Get the blob content from Azure Storage account and pass to Computer Vision (image content) for Azure Cognitive Service – Computer Vision to detect the animals/objects. Finally, write the API detection result in JSON format to Azure Storage account.

 

## End-to-End Process Flow (Orchestration)
The Logic App is used to orchestrate and loop through the images for animal detection using Azure Cognitive Service – Computer Vision.
 
## E2E with Custom/Computer Vision and Notification (Action)
The Logic App is used to orchestrate and loop through the images for animal detection using Azure Cognitive Service – Custom/Computer Vision with email notification.

 
