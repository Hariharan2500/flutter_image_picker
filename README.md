# Photo Picker in Flutter

This project demonstrates how to implement a photo picker in a Flutter application for selecting images from the device's photo library. It ensures seamless integration with both iOS and Android platforms, complying with platform-specific permission requirements.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Usage](#usage)
- [License](#license)
- [Author](#author)

## Features

- **Photo Selection:** Users can select photos from the device's gallery.
- **Cross-platform Support:** Fully functional on both Android and iOS.
- **Permission Handling:** Includes proper permission requests for accessing the photo library.
- **User-friendly Interface:** Clean UI for a smooth user experience.
- **Integration-ready:** Can be easily integrated into other Flutter projects.

## Technologies Used

- **Programming Language:** Dart
- **Framework:** Flutter
- **Photo Picker Library:** `image_picker` package
- **Others:** 
  - Flutter SDK
  - Android Studio / Visual Studio Code for development
  - Git for version control

## Installation

Follow these steps to set up the project locally:

```bash
# Clone the repository
git clone https://github.com/yourusername/photo-picker-flutter.git

# Navigate into the project directory
cd photo-picker-flutter

# Install dependencies
flutter pub get


```

**## Usage**

Below is an example of configuring the necessary iOS permissions in Info.plist:

```
<key>NSPhotoLibraryUsageDescription</key>
<string>We need access to your photo library to select images.</string>
<key>NSPhotoLibraryAddUsageDescription</key>
<string>We need permission to save images to your photo library.</string>

```
Add this code to your Flutter app for photo selection functionality:

```
import 'package:flutter/material.dart';
import 'package:image_picker/image_picker.dart';

class PhotoPickerDemo extends StatefulWidget {
  @override
  _PhotoPickerDemoState createState() => _PhotoPickerDemoState();
}

class _PhotoPickerDemoState extends State<PhotoPickerDemo> {
  final ImagePicker _picker = ImagePicker();
  XFile? _selectedImage;

  Future<void> pickImage() async {
    final XFile? image = await _picker.pickImage(source: ImageSource.gallery);
    setState(() {
      _selectedImage = image;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar:AppBar(title: Text('Photo Picker')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            if (_selectedImage != null)
              Image.file(File(_selectedImage!.path)),
            ElevatedButton(
              onPressed: pickImage,
              child: Text('Pick an Image'),
            ),
          ],
        ),
      ),
    );
  }
}

```
**## License**

This project is licensed under the MIT License, allowing free use, modification, and distribution. See the LICENSE file for more details.

**## Author**

**Hariharan Sivakumar**
www.linkedin.com/in/hariharaa
