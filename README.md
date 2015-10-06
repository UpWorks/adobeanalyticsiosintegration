# Adobe Analytics iOS Integration into Swift 2 Project
Adobe Analytics Integration into iOS Swift Applications

Currently, official documentation from Adobe for integrating the Objective-C Adobe Mobile Analytics SDK into a iOS Swift project does not exist.

Below is my experience in doing so and invite others to comment or provide pull requests.

Prerequisite Complete the two steps:

1. Set up your App in Adobe Mobile Services
2. Download the SDK and Testing Tools

Documentation located here: https://marketing.adobe.com/resources/help/en_US/mobile/ios/requirements.html

Step 1. Create a new group folder

Within your Xcode project create a new group titled Frameworks. Note if you are working with an existing project and have a folder group named something else where your included libraries are stored, skip this step.

Step 2. Import the Adobe Mobile Library

Open finder and locate the folder, `AdobeMobileLibrary` folder. This is located in the unzipped package you downloaded from the Prerequisite step above. Drag this folder into the Frameworks folder, or your own similarly named folder. In doing so you will be presented with a dialog to Choose options for adding these files.  For the Destination option, tick the Copy items if needed box.  For the Added folders option, Select Create groups. Add to all targets necessary, project and testing. Click the finish button.

Steps 3. Remove unneeded files from library

Delete the `AdobeMobileLibrary_Extension.a` and `AdobeMobileLibrary_Watch.a` files. *Do not perform this step if, you are building an Extension or Watch application.

Step 4. Add the SystemConfiguration.framework to the project

Add the `SystemConfiguration.framework` to the project by clicking on your project file in the Project Navigator, followed bu clicking on the General tab and selecting the project target. Next, click on the Linked Frameworks and Libraries plus, +, button.   This will present a dialog of available libraries and frameworks. In the Search box begin typing SystemC and select the SystemConfiguration.framework and click the Add button at bottom right of the dialog.

![alt text](https://dl.dropboxusercontent.com/u/2624610/tutorial-imgs/linking-framework-1.jpg "Screen Shot 1")

Step 5. Adding `libsqlite3.dylib`

Add the `libsqlite3.dylib` by clicking on the same Linked Frameworks and Libraries plus, +, button.  This time click the Add Other button on the bottom left of the dialog. This will bring up a file dialog. Press CMD + Shift + G. This will present the Go to the folder dialog, here enter `/usr/lib/`. This will present a new list of files, select the `libsqlite3.dylib` and click open in the lower right. This will add the lib to your Frameworks group.

Step 6. Create a Bridging Header

Right-click on your project's group folder within the project navigator and select new file, in the Choose a template for your new file dialog, select iOS Source and choose the Header file template. In the Save as dialog, name the file ADBMobile-Bridging-Header, this will create the file.

Step 7. Edit the Bridging Header

Open the file and and in between the `#define ADBMobile_Bridging_Header_h` and `#endif /* ADBMobile_Bridging_Header_h */` lines of code, add the following line of code: `#import "ADBMobile.h"`  Press CMD + B and ensure the project builds with no errors.

Step 8. Add Bridging Header to Project Build Settings

Click on the project file within the Project navigator and select the Build Settings tab.  In the search box, type swift, doing so will present you with the Swift Compiler - Code Generation options. Ensure your application group folder is expanded and the 'ADBMobile_Bridging_Header_h' file is visible.  Next on the line that reads Objective-C Bridging Header, place your mouse cursor in the column that reads your applications name and double click. You will be presented with a dialog that resembles a tool tip with a large open text area. Now drag the `ADBMobile_Bridging_Header_h` to this dialog and then press enter. Type CMD + B to ensure the project builds with no errors.

Step 9. Add Debug Logging

Open your project's AppDelegate.swift file and add the below line to the application method.
`ADBMobile.setDebugLogging(true)`

Type CMD + B to ensure the project builds with no errors.  Now type CMD + R and you will see the Adobe Mobile debugging info in the console.

Congratulations you have successfully integrated [Adobe's Marking Cloud Mobile Analytics](https://marketing.adobe.com/resources/help/en_US/mobile/ios/) into your iOS Swift project.

If you have updated information or a more preferred way of integrating the product please share through a pull request.

