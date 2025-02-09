# flutter_qrcode
Source code from my lecture about [QRCode in Flutter](https://github.com/abdazzamajhari/qr_safe) on 6th February 2025.
📝 source: Sesi 14, Abdul Azzam Ajhari, S.Kom., M.Kom. 

Thank you pak perkenalan Flutter-nya.

## Instal & Troubeshoot
Following the instructions in session 14, here are the results on my Mac.
via terminal;
### 1. Make sure basic flutter is running normally & devices are connected;
- `flutter doctor --android-licenses`
- `flutter doctor -v`
- `flutter devices`
  Found 3 connected devices:
  SM A235F (mobile) • RRXXXXXXX1W • android-arm64  • Android 14 (API 34)
  <- My Samsung has been detected

### 2. Upgrade the latest pubspec.yaml dependency;
- `flutter pub add qr_code_scanner`
- `flutter pub add http`

### 3. In the `gradle-wrapper.properties` file, the Gradle version, must be upgraded to version `gradle-8.10`, because my java version `openjdk 23.0.2 2025-01-21`.
- Add this in the `gradle-wrapper.properties` file: `distributionUrl=https\://services.gradle.org/distributions/gradle-8.10-all.zip`
- `flutter clean\nflutter pub get`
- `flutter run`

### 4. This issue about `namespace` between `AndroidManifest.xml` and `build.gradle` in the `qr_code_scanner` package.
On debug mode:
`What went wrong:
A problem occurred configuring project ':qr_code_scanner'.
Could not create an instance of type com.android.build.api.variant.impl.LibraryVariantBuilderImpl. 
Namespace not specified. Specify a namespace in the module's build file. See https://d.android.com/r/tools/upgrade-assistant/set-namespace for information about setting the namespace. 
If you've specified the package attribute in the source AndroidManifest.xml, you can use the AGP Upgrade Assistant to migrate to the namespace value in the build file. Refer to https://d.android.com/r/tools/upgrade-assistant/agp-upgrade-assistant for general information about using the AGP Upgrade Assistant.`

The solution is to add the `patch-1` to the `pubspec.yaml` file.
`qr_code_scanner:
git:
url: https://github.com/asmrtfm/qr_code_scanner
ref: patch-1
version: ^1.0.0`

Then, `rm -rf ~/.pub-cache/` `flutter clean` `flutter pub get` `rm -rf build/` `flutter run` again.

## References:
- https://github.com/abdazzamajhari/qr_safe
- https://docs.gradle.org/current/userguide/gradle_wrapper.html
- https://docs.gradle.org/current/userguide/compatibility.html#java_runtime
- https://github.com/juliuscanute/qr_code_scanner/issues/744
