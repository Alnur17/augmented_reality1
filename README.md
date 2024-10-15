# augmented_reality1

Check the link for better understanding:
https://docs.google.com/document/d/1sCBKMTNtFP187U0fFQEuJnYe0rnAoP-pXMHXKXwZ814/edit?usp=sharing

Project Documentation: Flutter 3D Object Viewer using model_viewer_plus
Overview
This Flutter project demonstrates how to display a 3D object using the model_viewer_plus package.
The app allows users to view and interact with the 3D object with features such as auto-rotation,
disabling zoom, and Augmented Reality (AR) viewing.
The 3D object used in this example is a .glb file named BrainStem.glb, which is stored in the assets
folder.

Features
3D Object Viewing: Display 3D objects using the ModelViewer widget.
Auto-Rotate: Enable continuous rotation of the 3D model.
Zoom Control: Option to disable zoom for a static view.
Augmented Reality (AR): View the 3D object on real-world surfaces when AR is enabled.

Technologies Used
Flutter: The frontend framework for building the app.
Dart: Programming language used within the Flutter framework.
model_viewer_plus: Flutter package for 3D object viewing and AR integration.

Folder Structure
Ensure your project has the following folder structure:
lib/
├── main.dart # Entry point of the app
assets/
└── images/
└── BrainStem.glb # 3D object file

Update your pubspec.yaml to include the assets:
flutter:
assets:

- assets/images/BrainStem.glb

Dependencies
Add the required dependencies to your pubspec.yaml:
dependencies:
flutter:
sdk: flutter
model_viewer_plus: ^1.9.0

Run flutter pub get to install the dependencies.

Code Example
Here’s a simple code setup to display a 3D object using the model_viewer_plus package:
import 'package:flutter/material.dart';
import 'package:model_viewer_plus/model_viewer_plus.dart';

void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
const MyApp({super.key});

@override
Widget build(BuildContext context) {
return MaterialApp(
debugShowCheckedModeBanner: false,
home: Scaffold(
appBar: AppBar(title: const Text('Model Viewer')),
body: const ModelViewer(
backgroundColor: Color.fromARGB(0xFF, 0xEE, 0xEE, 0xEE),
src: 'assets/images/BrainStem.glb',
autoRotate: true,
disableZoom: true,
ar: true, // Disable AR for testing
),
),
);
}
}

Android-Specific Configuration
To properly configure AR and networking permissions on Android, follow the steps below.

1. Android Manifest Changes
   Open AndroidManifest.xml and make the following changes:
   <application
   android:name="${applicationName}"
   android:icon="@mipmap/ic_launcher"
   android:label="example"
   android:usesCleartextTraffic="true">
   <activity android:name=".MainActivity">
   </activity>
   </application>

2. Build Gradle Changes
   In your app/build.gradle file, update the minimum SDK version:
   defaultConfig {
   ...
   minSdkVersion 21
   ...
   }

These changes ensure that the app supports AR and can make cleartext traffic requests.

iOS-Specific Configuration
For iOS, update the Info.plist file to request camera access for AR:

<key>NSCameraUsageDescription</key>
<string>We need camera access to display AR content</string>

AR Permissions
For Android: Ensure you have added the following permissions in your AndroidManifest.xml:
<uses-feature android:name="android.hardware.camera.ar" />
<uses-permission android:name="android.permission.CAMERA" />

For iOS: Add the camera usage description in your Info.plist:
<key>NSCameraUsageDescription</key>
<string>We need camera access to display AR content</string>

Installation Guide
Clone or download the project to your local machine.
Open the project in your preferred IDE or code editor.
Run the following command to install dependencies:

flutter pub get
Run the app on your device using:

flutter run

Additional Notes
Make sure you have a physical device with ARCore (Android) or ARKit (iOS) support for AR features.
For testing without AR, you can set ar: false in the ModelViewer widget.


