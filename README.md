# Stocklite

Stocklite is a mobile application built with Flutter to help manage inventory for pantry items, household products, or small business stock. The project provides a simple and clean experience for registering products, tracking quantities, identifying low-stock items, organizing categories and suppliers, and keeping everything synchronized with Firebase in real time.

The project is structured with a simple architecture based on screens, controllers, and services, separating responsibilities to make maintenance, expansion, and understanding of the data flow easier. It combines user authentication, NoSQL persistence with Firestore, and a modern interface using Material 3.

## What the project does

The app offers a complete inventory management flow, including:

- Create, edit, and delete products.
- Track available stock quantities.
- Define a minimum quantity to warn when items need restocking.
- Estimate restocking cost based on products below the minimum threshold.
- Search products by name.
- Filter products by category.
- Sort products by name or price.
- Switch between list and grid views.
- Manage categories and suppliers.
- Visually identify low-stock products.
- Search product names using barcode input through the public OpenFoodFacts API.
- Authenticate users with login, signup, password recovery, and strong password validation.
- Store data per user, ensuring isolation in Firebase.

## What the project is

Stocklite is an inventory management app focused on usability and simplicity. It was designed for people who need to control household items, small consumer stock, products used in light commercial routines, or a basic personal inventory.

The application is not a full ERP, but a lightweight, practical, and accessible solution for basic stock control tasks. It combines product registration, search, organization, and monitoring in a simple and responsive flow.

## Main features

### 1. Authentication and user accounts

The app includes a complete authentication flow:

- Login screen with email and password.
- Signup screen with name, phone, email, and password.
- Strong password validation: minimum length, uppercase letter, lowercase letter, number, and special character.
- Password recovery via Firebase Auth email sending.
- Storage of additional user information in Firestore.

### 2. Product management

On the main screen, the user can:

- Add a new product with name, price, quantity, minimum quantity, category, and supplier.
- Edit an existing product.
- Delete a product with confirmation.
- Adjust the quantity using + and - buttons.
- See whether an item is low in stock.

### 3. Search, filters, and organization

The catalog screen allows:

- Search products by name.
- Filter products by category.
- Switch between list and grid views.
- Sort products by name ascending/descending and price ascending/descending.

### 4. Category and supplier management

The summary module allows:

- Create categories.
- Edit categories.
- Delete categories.
- Create suppliers.
- Edit suppliers.
- Delete suppliers.

This information is used to organize registered products and improve catalog navigation.

### 5. Restocking alerts

The summary screen shows:

- Total number of unique products registered.
- Estimated cost to restock items below minimum stock.
- A list of products with low or minimum-level stock.

### 6. Barcode integration

The product registration screen includes a barcode field. When searched, the app queries the OpenFoodFacts API to try to retrieve the product name automatically. This makes product entry faster and easier.

## Project structure

The main structure of the project is organized as follows:

- lib/main.dart: application entry point.
- lib/modules/auth: authentication, signup, and password recovery screens and controllers.
- lib/modules/home: main app screens and controllers, including catalog, summary, search, and add/edit product flows.
- lib/modules/about: project information screen.
- lib/data/models: data models such as product, category, and supplier.
- lib/data/services: services for communication with Firebase Firestore and persistence logic.
- lib/firebase_options.dart: Firebase configuration for each platform.

## Technologies and libraries used

The project mainly uses:

- Flutter and Dart.
- Material 3 for the interface.
- Firebase Authentication for user authentication.
- Cloud Firestore for data storage.
- Provider for simple state management.
- Device Preview for interface preview during development.
- intl_phone_number_input for phone input with country selection.
- http for integration with the OpenFoodFacts API.

## Requirements to run the project

Before running the project, you will need:

- Flutter SDK 3.8.1 or newer.
- A Dart SDK compatible with the installed Flutter version.
- Android Studio or VS Code with Flutter and Dart extensions.
- An Android emulator or a physical Android device connected.
- Optionally, Xcode if you want to run on iOS on macOS.
- A Firebase account.
- Git to clone the repository.

## How to install Flutter

If Flutter is not installed yet, follow the official steps:

1. Visit the Flutter website.
2. Download the stable version compatible with your operating system.
3. Extract the SDK to a folder of your choice.
4. Add Flutter to your system PATH.
5. Run:

```bash
flutter doctor
```

This validates whether all required dependencies are properly configured.

## How to run the project

### 1. Clone the repository

```bash
git clone <repository-url>
cd STOCKLITE
```

### 2. Install dependencies

```bash
flutter pub get
```

### 3. Check that the environment is ready

```bash
flutter doctor
```

### 4. Configure Firebase

This project already includes a Firebase configuration file at [lib/firebase_options.dart](lib/firebase_options.dart), but it is important to ensure that it matches your real Firebase project.

If you are using a different Firebase project, it is recommended to regenerate the options with FlutterFire:

```bash
flutterfire configure
```

Also make sure that:

- the Firebase project exists;
- Authentication is enabled for email/password;
- Firestore is enabled;
- google-services.json is configured for Android;
- GoogleService-Info.plist is configured for iOS.

### 5. Run the app

For Android:

```bash
flutter run
```

Or for a specific device:

```bash
flutter run -d <device-id>
```

For web:

```bash
flutter run -d chrome
```

If an Android emulator is already running:

```bash
flutter devices
flutter run -d <emulator>
```

## Firebase data structure

The app uses Firestore with the following organization:

- users collection
  - One document per authenticated user
  - products subcollection: user products
  - categories subcollection: user categories
  - suppliers subcollection: user suppliers

This structure ensures that each account has its own isolated data.

## Important notes

- The project uses real authentication, so a user must create an account before using the app fully.
- The app depends on a Firebase connection to create accounts, log in, save products, and synchronize data.
- The OpenFoodFacts API integration depends on internet access and may not return results for every product.
- For development, Device Preview is active in non-release mode.

## Useful commands

To clean and reinstall dependencies:

```bash
flutter clean
flutter pub get
```

To validate the project after changes:

```bash
flutter analyze
```

## One-line summary

Stocklite is a Flutter app for managing product inventory with authentication, Firebase persistence, category/supplier organization, and low-stock alerts.
