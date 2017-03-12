# Hack101: Introduction to iOS Development #

### Your First iOS App 

Hello, and welcome to the iOS Tutorial. Today we will be covering the basics of iOS Development and make our very own app, a Tip Calculator!

 In this tutorial, you will learn about using Xcode, building interfaces with auto-layout, and how to get an app running on your phone! This tutorial will assume a basic knowledge of Object Oriented programming and how some data types work in Swift. Dont worry if you are completely new to the language! Here are some resources that cover the required knowledge for this tutorial.

### Initial Setup ###

So without further ado, lets begin coding our application. 

* 1 Open Xcode
* 2 From the File menu, select New and then Project
* 3 Under iOS, within the Application section, select Single View Application, and click Next

![Choose App Type](https://github.com/arunrawlani/iOSTutorial_HackMcGill/blob/master/Images%20for%20Tutorial/choseapp.png)

* 4 Enter "Tip Calculator" for the Product Name
* 5 For Team, you can select your Apple Developer Team if you have one, or simply leave it as None.
* 6 For Organization Name, you can enter your own name
* 7 Leave the organization identifier as it is
* 8 Select Swift as the Language and iPhone as the device

![App Info](https://github.com/arunrawlani/iOSTutorial_HackMcGill/blob/master/Images%20for%20Tutorial/appinfo.png)

* 9 Click Next and navigate to the place on your computer where you keep projects. Don't worry about naming the folder or anything like that, Xcode will handle it for you.
* 10 Keep the Create Git Repository on My Mac checkbox selected, and click Create

Awesome, so now you've created your first project file using XCode and our next step is to start making our Tip Calculator iOS App!

### Your First iOS App UI ###

####Interface Builder & Story Board####

So there are two different ways of designing UIs for iOS applications. You can do it programmatically with code or, you can do it graphically using the Story Board and the integrated Interface Builder. Yes, this is the tool first released in 1988 by Apple and its better than ever!

The only time you would want to do your UI programmatically is when you are working on a big project and multiple changes on the Story Board can lead to merge conflicts. So keep this in mind if you are doing this at a hackathon with four other people.

Select Main.storyboard from the project navigator. Right next to the Project Navigator is the Story Baord Navigator. It lists all the screens and UI elements you currently have in your Story Board. By default you have one View Controller on the Story Board. The gray arrow right next to it indicates the initiation point of the app.

So lets fire up the simulator and see where the app currently stands. All you can see is a blank screen which is the View Controller on the StoryBoard. Now we will proceed by adding UI components to the View Controller.

####Adding UILabel to the View Controller####

Now lets add some text to our View Controller. The text holder UI Element in iOS is called UILabel.

* 1 On the bottom right of the screen, in the Object Browser, scroll until you find UILabel
* 2 Drag and drop the label component onto your View Controller in the Story Board. Make sure it is in the center. Two dashed blue lines will appear indicating the center. You might need to zoom into the Storyboard if it won't let you drag the label in (pinch out on the trackpad)

![Adding Label](https://github.com/arunrawlani/iOSTutorial_HackMcGill/blob/master/Images%20for%20Tutorial/putlabel.png)

* 3 To change the text in the label, look at Utilities Panel on the right of your XCode screen and choose the Attributes Inspector section in it.
* 4 In the second field in your Attributes Inspector, change "Label" to "Tip Calculator" and press enter. Now you've changed the text in the label.

![Small Label](https://github.com/arunrawlani/iOSTutorial_HackMcGill/blob/master/Images%20for%20Tutorial/smalllabel.png)

But damn! The label seems to be too small to display the whole text. We can simply drag the label to display the text but instead we are going to use this opportunity to get started with the most powerful part of Interface Builder that developers would have killed for back in the 90s.

####Auto Layout and Screen Constraints####

Recently, Apple released Auto Layout to allow developers to build iOS apps without caring too much about the different screen sizes. With Auto Layout, you have to set constraints with respect to your UI elements and allow these contraints to adapt to different screen sizes while maintaing your interface layout. 

Auto Layout is an extremely powerful tool. And because great power comes with great responsibility, you need to spend some hours to get yourself accustomed with the tool. Some good resources to learn more about Auto Layout are:
* 1 https://developer.apple.com/library/content/documentation/UserExperience/Conceptual/AutolayoutPG/
* 2 Video from Stanford's course on iOS Development: https://www.youtube.com/watch?v=wBzzfaTj4vg

So now that we know what Auto Layout is, lets use it for our project and put some contraints on the label element we have in our view controller.

* 1 With the label selected, hold "control" while clicking and dragging upwards. Let go and hold "option" so you can click Top space to container margin.
* 2 With the label still selected, control-click drag from the label to the parent View. In the menu that appears, select Equal Widths.
* 3 With the label still selected, press the Pin button at the bottom of the Story Board screen
* 4 Check height and set it to 80. Then click add 1 constraint. 
* 5 Click the Resolve Auto Layout Issues button at the bottom of the storyboard on the right of the Pin button. Then click update frames.
* 6 While your label is still selected, go back to your Attributes Inspector and set the label Alignment to Center.

So what we did in the steps above is to add constraints such that our label is sitting 0 pixels from the top, right and left. These numbers are not arbitrary but part of Apple's Human Interface Guidelines which you should definitely look into after this tutorial.

####Adding other UI Elements to the App####

Now lets add more UI elements to our Tip Calculator. We will be using UILabel and UITextFields.

* 1 Drag a label from the Object Browser onto the screen (slight below the top label and just a bit left of center)
* 2 Drag a textfield from the Object Browser onto the screen (slight below the top label and just a bit right of center)
* 3 Select both the label and the textfield using by pressing the "command" key and clicking on both of them.
* 4 While both of them are selected, press "option" and make a copy of the label and textfield. Place it a little below the original one. Repeat until you have 4 pairs.
* 5 Drag a button from the Object Browser, and add it to the center of the screen below all the pairs.
* 6 Click on the second text field to select it. Press delete on your keyboard to delete it.
* 7 Drag a Segmented Control from the Object Browser into its place (use the guides to position it).
* 8 In the Attributes Inspector, change the segments from 2 to 3.

Now run the simulator. The fields seems completely off. This is because we havent set constraints for them yet. 

####Setting constraints for the Added Elements####

So to make sure that all the textfields look the same lets set some constraints for them.

* 1 Click on the first text field to select it.
* 2 Hold shift and click on the other two text fields to select them as well. Not the segmented control.
* 3 Open the pin menu, check width, enter 85 and click add 3 constraints to apply the changes.
* 4 Click on the segmented control and do the same but set the width to 125

If you check using the simulator, the constraints are still broken. We will be fixing them using Stacked Views.

####Using Stacked Views####

To make it easier to manage our layout, we will be using Stacked Views. Stack views are used to align elements vertically or horizontally. Each pair of label and text field / segmented control will be added to a horizontal stack view. All these "rows" and the button will then be added to a single vertical stack view.

* 1 Click on the first label to select it. Hold shift and click on the text field to its right.
* 2 Click the stack button (rectangles with down arrow, near pin button) to combine them in a horizontal stack view. You should see them squish together and form one unit.
* 3 Repeat for the other three label and text field/segmented control pairs.

Now you have created 4 stack views. We will now be creating a super stacked view with all the smaller stacked views. We will be doing that using the Story Board Panel on the left, next to the Navigator Panel. Do not try to select the smaller stacks directly through the Story Board as we did above.

* 1 In the Story Board Panel, select all 4 Stack Views using the shift or command button. Once all 4 are selected then click the stack button (rectangles with down arrow, near pin button) to form the super stacked view.

####Organizing the Layout Tree####

Now lets organize our labels and textfields by inputting the correct text before moving on to finalizing the constraints.

* 1 Look at the Story Board Panel again. Click once to select the root stack view, pause, click again to edit its name. Enter "Super Stack View". From now on, we'll refer to this process as "rename the element".
* 2 Rename the first horizontal stack view to Bill Amount Stack View.
* 3 Select the first label and change its text to Bill Amount: from the attribute inspector.
* 4 Rename the first text field to Bill Amount Text Field
* 5 Rename the second horizontal stack view to Tip % Stack View, change its label's text to Tip %:, and rename its segmented controller to Tip % Segmented Controller.
* 6 Rename the third horizontal stack view to Tip Amount Stack View, change its label's text to Tip Amount:, and rename its text field to Tip Amount Text Field.
* 7 Rename the fourth horizontal stack view to Total Stack View, change its label's text to Total:, and rename its text field to Total Text Field.
* 8 Select the button and change its title to Calculate from the attribute inspector.
* 9 Select the segmented view element. Then for Segment 0 change title to 15%, then click on Segment and select segment 1. Then change its title to 18%. Then do the same thing for segment 2 and put 20% as the value.

Final result should like like the following:

![Layout Tree](https://github.com/arunrawlani/iOSTutorial_HackMcGill/blob/master/Images%20for%20Tutorial/layouttree.png)

Now we are very close to finishing the UI of our app. So exciting! We have our very own tip calculator UI in under 2 hours. 

Now lets add some more constraints to the Super Stacked View to finalize everything:

* 1 Select the Super Stacked View in the Story Board Panel and then set spacing to 20 in the Attributes Inspector (on the right of the XCode screen).
* 2 While the Super Stacked View is selected, open the pin menu.
* 3 Activate the left, top, and right constraints. Set the left and right to 50. Set the top to 20.
* 4 Click on the Resolve Auto Layout Issues button next to the pin button and press Update Frames.

Now to make sure that the individual components in the smaller stacked are not squished anymore, lets add a few more constraints:
* 1 Select Bill Amount Stack View in the Story Board panel, control-click (or right-click) drag from the Bill Amount Stack View to the Super Stack View and, in the menu that appears, select Equal Widths. This will ensure that the row is always the same width as the Super Stack View.
* 2 Repeat this process for each other stack view row and the Calculate button.
* 3 If a read line appears this means that there is a constraint conflict. Press the red button that appears in the Story Board Panel. This opens up suggestions to resolve the constraints issue. Add a constraint for the Y axis and update the frames. This will fix it.

After the steps above your Story Board should look similar to this:

![Storyboard Layout](https://github.com/arunrawlani/iOSTutorial_HackMcGill/blob/master/Images%20for%20Tutorial/storyboard.png)

Aweeeesomeeee! So now we have completed the UI for our app. Lets fire up the simulator to see our app and it should look like a tip calculator. The only thing left is to add logic to calculate the tip!

### Adding Logic for your App ###

####Linking your interface to code####
Now that we have a UI, lets add code for our app to finish our application. XCode allows you to connect your interface layout with the code using the Assistant Editor which we will now be using.

So first a little information on what these connections are:
There are two main kinds of code connections: outlets, and actions. Outlets let you assign a variable in code to a component of your interface you have created in your storyboard to interact with that component in code. We will use that to read and set values from our interface. Actions let our code know when the user did certain things to an interface component that we want to react to.

### Adding Code Connections ###
* 1 Close the layout tree and attribute inspector to make some room.
* 2 Open the assistant editor and make sure ViewController.swift is displayed by switching from "Preview" to "Automatic" in the dropdown menu above the assistant editor view window.
* 3 Control-click (or right-click) drag from bill amount text field to under the class ViewController line and name the outlet billAmountField.
* 4 Control-click (or right-click) drag from the tip selector text field and name the outlet tipSelector.
* 5 Control-click (or right-click) drag from the tip amount text field and name the outlet tipAmountField.
* 6 Control-click (or right-click) drag from the total amount text field and name the outlet totalAmountField.
* 7 Control-click (or right-click) drag from the calculate button to the view controller. Choose Action and name it calculateTip.

Final result should look like the following:

![Code Connections](https://github.com/arunrawlani/iOSTutorial_HackMcGill/blob/master/Images%20for%20Tutorial/codeconnect.png)

####Adding the Code to Calculate Tip####

So now lets talk a little bit about if let statements in Swift before we jump onto writing the code. "if let" is a special statement that allows us to check the condition of a variable and perform actions based on that condition. In the code below, we are saying if you can cast billAmount to a Double and save it to a new variable called billAmount, then do nothing. However, if you cannot do this, then we should stop what we are doing and clear the fields". If the condition is met, then the function can continue.


So lets add this code to our IBAction calculateTip that we created in the last step:

```swift
    @IBAction func calculateTip(sender: AnyObject) {
    if let billAmount = Double(billAmountField.text!) {
        var tipPercentage = 0.0

        switch tipSelector.selectedSegmentIndex {
        case 0:
            tipPercentage = 0.15
        case 1:
            tipPercentage = 0.18
        case 2:
            tipPercentage = 0.20
        default:
            break
        }

        let roundedBillAmount = round(100 * billAmount) / 100
        let tipAmount = roundedBillAmount * tipPercentage
        let roundedTipAmount = round(100*tipAmount)/100
        let totalAmount = roundedBillAmount + roundedTipAmount

        if (!billAmountField.isEditing) {
            billAmountField.text = String(format: "%.2f", roundedBillAmount)
        }
        tipAmountField.text = String(format: "%.2f", roundedTipAmount)
        totalAmountField.text = String(format: "%.2f", totalAmount)
    } else {
        //show error
        billAmountField.text = ""
        tipAmountField.text = ""
        totalAmountField.text = ""
    }
}
```
Once the code is added. Lets run the app. If everything is working fine then well.....Congratulations! You have created your very first iOS application. Your next steps could be to customize the design a bit. Add more options for tipping e.g. a custom option maybe.

I have shared few resources below that can help your understanding of the Swift Code and iOS development even more. Feel free to shoot me a message at arun.rawlani@mail.mcgill.ca if you have any questions.

Happy Tipping! 

##Additional Resources##
* 1 Probably the best resource on the internet to start off with iOS Application Development: https://www.raywenderlich.com/
* 2 Apple's WWDC wesbite. Has videos for all the new libraries released for every year. Has presentations from Apple Engineers who give brief demos on how to use these new libraries. Extremely useful if you are diving into a lot of the native libraries for iOS Development: https://developer.apple.com/videos/
