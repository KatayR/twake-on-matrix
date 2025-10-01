Build Instructions for New PC

  Prerequisites

  1. Install Flutter 3.27.4
  2. Install Android Studio (for Android builds)
  3. Install Xcode (for iOS builds, macOS only)
  4. Install CocoaPods (for iOS, macOS only): sudo gem install cocoapods

  Building for Android

  # 1. Get Flutter dependencies
  flutter pub get

  # 2. Generate required code files (important!)
  flutter pub run build_runner build --delete-conflicting-outputs

  # 3. Build debug APK (no signing required)
  flutter build apk --debug
  # Output: build/app/outputs/flutter-apk/app-debug.apk

  # OPTIONAL: 
  # 4. For release APK (requires signing setup)
  # First, create android/key.properties file with:
  #   storeFile=path/to/keystore.jks
  #   storePassword=your_password
  #   keyAlias=your_alias
  #   keyPassword=your_password
  # Then run:
  # flutter build apk





  Building for iOS (macOS only)

  # 1. Get Flutter dependencies
  flutter pub get

  # 2. Generate required code files (if not already done)
  flutter pub run build_runner build --delete-conflicting-outputs

  # 3. Install CocoaPods dependencies
  cd ios && pod install && cd ..

  # 4. Run on simulator
  # First, list available simulators:
  xcrun simctl list devices

  # Then run on a specific simulator:
  flutter run -d <DEVICE_ID>
  # Or just run on any available device:
  flutter run

  Key Changes Made

  - No code changes were required
  - Generated files: The build_runner command generated .g.dart files that were missing (required for JSON serialization)

  Common Issues

  1. Android release build fails: Missing key.properties file - use debug build instead
  2. Missing generated files: Run flutter pub run build_runner build --delete-conflicting-outputs
  3. iOS pod install issues: Delete ios/Podfile.lock and ios/Pods/, then run pod install again