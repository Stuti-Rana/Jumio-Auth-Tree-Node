Jumio Cloud Nodes 
This is a reference manual and configuration guide for the Netverify integration with Forgerock Identity Cloud. 
What is Jumio ID Verification?
Jumio's ID Verification allows customers to easily and securely capture and submit their government-issued ID documents. It performs real-time ID verification using machine learning, helping you deter fraud and meet regulatory requirements. 
Jumio validates the user’s ID, corroborates it with a selfie and uses advanced liveness detection to ensure the person is actually present. 
Nodes Description 
Jumio Initiate Node- This node will initiate Jumio’s NetVerify service. This service will scan a user’s ID as well as their face to verify their identity.
Jumio Decision Node- This node will decide if the user is able to successfully login depending on the validity of their NetVerify scan. If the NetVerify service is able to successfully validate the user’s identity, they will be successfully authenticated. In the case of unreadable scans or unsupported types they will be led back to the Initiate node to redo the NetVerify process. And finally in the case of failed or fraud detection, the user will be met with a login failure. 
Set up the Jumio Service in ForgeRock Cloud
Sign into the Jumio Customer Portal 

In the toggle menu on the left hand sign go to Settings > Managed Services > Identity Verification.
 
Go to API Credentials > OAuth2 Clients

Click ‘Generate a new API token’ and select both the ‘Initialize’ and ‘Retrieve & Delete’ permissions.

Login to the ForgeRock Cloud tenant. 
In the left-hand side toggle menu select Access Management.

Go to ‘Realms’ them, on the left hand-side toggle menu select ‘Services’
In the drop-down menu for ‘Choose a service type’ select ‘Jumio Service’.
Configure the service by filling out the fields. For ‘Token’ and ‘Secret’ use the new API credentials generated from the Jumio Service. 
Configure the Tree in ForgeRock Cloud
 Go to the ForgeRock Cloud homepage > Journeys > + New Journey
 Name the Journey ‘i.e. JumioTest’ for Identity Object select ‘Alpha realm-    Users managed/alpha_user
Drag & drop the nodes to recreate the below tree:

Testing
To test the Journey, copy and paste the preview URL in an incognito window. 
Login using ForgeRock Cloud credentials and Jumio’s NetVerify Service will prompt the user to start the verification process. Click Start.



The user will be directed to select their Region and to select ID type. 

Take a photo of the front and back of the ID using the webcam or upload a photo from your computer

Once prompted, complete the face verification step.
If the verification is successful the user will be successfully authenticated.