# Day 2.3: Firebase Storage

So far, we have learnt how to store data such as strings, integers on our Realtime Database. However, what if we wanted to store something a little more complex, such as images? For example, let's say we want to give users the option to change the display image of their pets, and we want these images to be shared across any device they use, how should we go about doing that?

Firebase Storage is a great solution to this problem.

## Creating a Firebase Storage Bucket

1. Go to the Firebase Console Website, and look on the left for **Storage**.

![](../../imgs/gtc/android/storage_console.png)


2. Click on **Get Started**, click **Next**, and then select your Cloud Storage Location. Select `asia-southeast2` for the location, and press **Done**. After it is done loading, you should see something like this

![](../../imgs/gtc/android/firebase_storage.png)

3. You now have a Storage Bucket. Right now, our Firebase Storage only allows **Authenticated users** to access this storage. This is okay for us since our users need to be authenticated to use the app.

## Setting up Firebase Storage on our Android app

We'll need to add this line of dependency to the **module-level** `build.gradle` file, under `dependencies`:

```groovy
implementation 'com.google.firebase:firebase-storage'
```

As usual, remember to press **Sync now**

## Uploading a file to Firebase Storage

1. We will first need to configure our ImageViews in `MyPetActivity` to open a dialog for us to choose an Image to change to. To start off, create an onClickistener for each of other ImageViews, by pasting this code in the `initialiseWidgetsForPets` function.
   
    ```java
    petImage.setOnClickListener(view -> {
        
    });
    ```
2. Then will need to create an **Intent** to select an image. Similar to opening our FirebaseUI, we first need a request code for this intent. Copy the following to the top level of our `MyPetActivity` class.

    ```java
    private final static int RC_PICK_IMAGE = 1;
    ```

3. Now we need to actually create the intent. Inside our OnClickListener, copy this

    ```java
    Intent intent = new Intent();
    intent.setType("image/*");
    intent.setAction(Intent.ACTION_GET_CONTENT);
    startActivityForResult(Intent.createChooser(intent, "Select Picture"), RC_PICK_IMAGE);
    ```

4. Once again, we will need to listen for the result of our Image Picker Request, using the `OnActivityResultFunction`, and also check that the result indeed came from the image picker request. In our `MyPetActivity` class, type in the following function:

