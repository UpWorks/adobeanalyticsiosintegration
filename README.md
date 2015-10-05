# Adobe Analytics iOS Integration
Adobe Analytics Integration into iOS Swift Applications

Currently, official documentation from Adobe for integrating the Objective-C Adobe Mobile Analytics SDK into a iOS Swift project does not exist.

Below is my experience in doing so and invite others to comment or provide pull requests.

Prerequisite Complete the two steps:
+ Set up your App in Adobe Mobile Services
+ Download the SDK and Testing Tools
Documentation located here: https://marketing.adobe.com/resources/help/en_US/mobile/ios/requirements.html

Step 1. Within you Xcode project create a new group titled Frameworks. Note if you are working with an existing project and have a folder group named something else where your included libraries are stored, skip this step.

Step 2. Open finder and locate the folder, AdobeMobileLibrary folder. This is located in the unzipped package you downloaded from the Prerequisite step above. Drag this folder into the Frameworks folder, or your own similarly named folder. In doing so you will be presented with a dialog to Choose options for adding these files.  For the Destination option, tick the Copy items if needed box.  For the Added folders option, Select Create groups. Add to all targets necessary, project and testing. Click the finish button.

Steps 3. Delete the AdobeMobileLibrary_Extension.a and AdobeMobileLibrary_Watch.a files. Do not perform this step if, you are building an Extension app or Watch app.
