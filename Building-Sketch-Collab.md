Alright it's time for you to try to build Sketch Collab on your own machine.

If one of these steps are unclear, or you have some trouble in doing it, create a "question issue" in the issues page, I'm here to help!

Here are the steps to do it:
 - First of all, clone the repository by doing
   ```
   git clone https://github.com/Iyxan23/sk-collab
   ```
   Or, if you don't have git installed, you can just download the code directly by pressing the "Code" button and click "Download ZIP".

   Unzip the code and you're done.
 - Create a new Firebase Project (if you haven't already)

   Open up the [firebase console](https://console.firebase.google.com/), and click "Add project" (may depend on your language). Add a name for it, and bla bla bla.

 - Once you finished adding the project, Click on "Add Application" on the top, and choose Android. Set the package name as the package name you set (If you haven't set it, it should be com.iyxan23.sketch.collab), Set the application name as you like, in this example, I'll use "SketchCollab", and finally click the register app button.

 - Once you've done that, download the `google-services.json`. This file is super important, never share it to anybody.
 - After that, move that `google-services.json` file to the `app/` directory of sk-collab.
 - Then you can skip the next step and the next next step too.

 - After adding your app to your firebase project, you can go to the `Authentication` page, click the enable button (If you haven't already), click on Sign-In Method, and enable Email sign-in.
 - Now, let's set up the database, first, click on Firebase Firestore, click enable in it, and you can do some setups with it.
 - After enabling firebase firestore, create a collection named `status`, also create a document named `status` inside that `status` collection, Then create a field named "is_open", set it to be Boolean, and set it to be `true`. You also need to create a "reason" field, set it as String, and fill it as you like. This reason String will be displayed to the user if you set the "is_open" to be false (means that you close the server, possibly for maintenance or testing).
 - You're done! Open the project on android studio and run it, Congratulations, you've just built SketchCollab!