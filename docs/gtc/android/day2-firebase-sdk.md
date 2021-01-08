# Day 2 Part 1: Adding Firebase to your project

Before we are able to use any of Firebase services, you need to connect the Firebase Cloud to your project. Let's begin!

## Step 1: Create a Firebase Account

Go to <https://firebase.google.com>, and sign in with a Google account. After logging in, you should be redirected to <https://console.firebase.google.com/>. 

![](../../imgs/gtc/android/firebase_auth_add_project.jpg)


## Step 2: Create a Firebase Project

- Click on the big **Add Project Button**, and enter a project name for your application (I will use `PetApp`)
- The next screen will ask if you want to enable Google Analytics for your app. This doesn't really matter since we won't be using it, but I would just disable it for now.
- Go ahead and click **Create Project**
- Wait for it to be done and click **Continue**. You have now created your first Firebase Project!

![](../../imgs/gtc/android/firebase_project_created.png)

## Step 3: Linking the Firebase Project to your Android App

- Click on the **Android Icon** to add Firebase to Android
- The first field will ask you for your Android package name. To find it, go to the `build.gradle(Module:app)` file in your Android Studio project (It is found under `Gralde Scripts`). Look for the `applicationId`
- Fill in a nickname for `App nickname`
- 