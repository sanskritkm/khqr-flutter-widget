<div align="center">
  <h1 align="center" style="font-size: 50px;">🍃 KHQR SDK 🍃</h1>
</div>

> [!NOTE]
> This **KHQR SDK** plugin is not officially release from [**NBC**](https://bakong.nbc.gov.kh/).
> 
> This is a simple interface layer that connects your Dart code directly to the original native platform-specific SDK, bridging Flutter and native functionality seamlessly.
> 
> [KHQR SDK Document Reference](https://bakong.nbc.gov.kh/en/download/KHQR/integration/KHQR%20SDK%20Document.pdf)
---

<div align="center">
<p align="center">
The standardization of KHQR code specifications will help promote wider use of mobile retail payments in Cambodia and provide consistent user experience for merchants and consumers. It can enable interoperability in the payment industry. A common QR code would facilitate payments among different schemes, e-wallets and banks and would encourage small merchants to adopt KHQR code as payment method. KHQR is created for retail or remittance in Cambodia and Cross-Border. It only requires a single QR for receiving transactions from any payment provider through Bakong including Bakong App.
</p>
</div>

<div align="center">
   <!--  Donations -->
  <a href="https://ko-fi.com/mrrhak">
    <img width="300" src="https://user-images.githubusercontent.com/26390946/161375567-9e14cd0e-1675-4896-a576-a449b0bcd293.png">
  </a>
  <div align="center">
    <a href="https://www.buymeacoffee.com/mrrhak">
      <img width="150" alt="buymeacoffee" src="https://user-images.githubusercontent.com/26390946/161375563-69c634fd-89d2-45ac-addd-931b03996b34.png">
    </a>
    <a href="https://ko-fi.com/mrrhak">
      <img width="150" alt="Ko-fi" src="https://user-images.githubusercontent.com/26390946/161375565-e7d64410-bbcf-4a28-896b-7514e106478e.png">
    </a>
  </div>
  <!--  Donations -->
</div>

<div align="center">
  <a href="https://pub.dartlang.org/packages/khqr_sdk">
    <img src="https://img.shields.io/pub/v/khqr_sdk?label=Pub&logo=dart"
      alt="Pub Package" />
  </a>
  <a href="https://pub.dev/packages/khqr_sdk">
    <img src="https://img.shields.io/pub/likes/khqr_sdk?style=flat&logo=dart&label=Likes" alt="Pub Likes"/>
  </a>
  <a href="https://pub.dev/packages/khqr_sdk">
    <img alt="Pub Popularity" src="https://img.shields.io/pub/popularity/khqr_sdk?style=flat&logo=dart&label=Popularity&link=https%3A%2F%2Fpub.dev%2Fpackages%2Fkhqr_sdk">
  </a>
  <a href="https://pub.dartlang.org/packages/khqr_sdk/score">
    <img src="https://img.shields.io/pub/points/khqr_sdk?label=Score&logo=dart"
      alt="Pub Package" />
  </a>
  <a href="https://github.com/mrrhak/khqr_sdk"><img src="https://img.shields.io/github/stars/mrrhak/khqr_sdk.svg?style=flat&logo=github&colorB=deeppink&label=Stars" alt="Star on Github"></a>
  <a href="https://github.com/mrrhak/khqr_sdk"><img src="https://img.shields.io/github/forks/mrrhak/khqr_sdk?color=orange&label=Forks&logo=github" alt="Forks on Github"></a>
  <a href="https://github.com/mrrhak/khqr_sdk/graphs/contributors">
    <img src="https://img.shields.io/github/contributors/mrrhak/khqr_sdk.svg?style=flat&logo=github&colorB=yellow&label=Contributors"
      alt="Contributors" />
  </a>
  <a href="https://github.com/mrrhak/khqr_sdk/actions?query=workflow%3A">
    <img src="https://github.com/mrrhak/khqr_sdk/actions/workflows/format-analyze-test.yml/badge.svg"
      alt="Build Status" />
  </a>
  <a href="https://github.com/mrrhak/khqr_sdk">
    <img src="https://img.shields.io/github/languages/code-size/mrrhak/khqr_sdk?logo=github&color=blue&label=Size"
      alt="Code size" />
  </a>
  <a href="https://pub.dev/packages/khqr_sdk">
    <img src="https://img.shields.io/badge/Platform-Android%20|%20iOS%20-blue.svg?logo=flutter"
      alt="Platform" />
  </a>
</div>

---

<p align="center">
  <img src="assets/khqr_sdk_preview.png" width="500" alt="khqr sdk preview"/>
  <!-- <img src="https://raw.githubusercontent.com/mrrhak/khqr_sdk/master/assets/khqr_sdk_preview.png" width="500" alt="khqr sdk preview"/> -->
</p>

## Supported Platforms
- [x] iOS
- [x] Android
- [ ] Web
- [ ] MacOS
- [ ] Windows
- [ ] Linux

## Native KHQR SDK Version
- iOS using **`BakongKHQR`** (v1.0.0.15)
- Android using **`kh.gov.nbc.bakong_khqr:sdk-java:1.0.0.13`**


## Features
- **Core SDK**
  - [x] Generate KHQR (Individual / Merchant)
  - [x] Verification (Valid / Invalid)
  - [x] Decode KHQR Information
  - [x] Generate KHQR Deeplink
- **Widget**
  - [x] KHQR Card Widget


## Platform specific setup
### iOS
1. Add source to Podfile (ios/Podfile)
```bash
source "https://sambo:ycfXmxxRbyzEmozY9z6n@gitlab.nbc.gov.kh/khqr/khqr-ios-pod.git"
```

2. Run pod install (make sure your terminal is in ios folder)
```bash
pod install
```

### Android
- No need to do anything it's working out of the box.

## Usage
### Create instance of KHQR SDK
```dart
import 'package:khqr_sdk/khqr_sdk.dart';

final _khqrSdk = KhqrSdk();
```

### Generate KHQR (Individual)
```dart
final info = IndividualInfo(
  bakongAccountId: 'john_smith@devb',
  merchantName: 'John Smith',
);
final khqrData = await _khqrSdk.generateIndividual(info);
```

### Generate KHQR (Merchant)
```dart
final info = MerchantInfo(
  bakongAccountId: 'john_smith@devb',
  acquiringBank: 'Dev Bank',
  merchantId: '123456',
  merchantName: 'John Smith',
);
final khqrData = await _khqrSdk.generateMerchant(info);
```

### Verify KHQR
```dart
const qrCode = '00020101021129190015john_smith@devb5204599953031165802KH5910John Smith6010Phnom Penh991700131727168754698630499FB';
final isValid = await _khqrSdk.verify(qrCode);
```

### Decode KHQR
```dart
const qrCode = '00020101021129190015john_smith@devb5204599953031165802KH5910John Smith6010Phnom Penh991700131727168754698630499FB';
final khqrDecodeData = await _khqrSdk.decode(qrCode);
```

### Generate KHQR Deeplink
```dart
const qrCode = '00020101021129190015john_smith@devb5204599953031165802KH5910John Smith6010Phnom Penh991700131727168754698630499FB';

final sourceInfo = SourceInfo(
  appName: 'Example App',
  appIconUrl: 'http://cdn.example.com/icons.logo.png',
  appDeepLinkCallBack: 'http://app.example.com',
);

final deeplinkInfo = DeeplinkInfo(
  qr: qrCode,
  url: 'http://api.example.com/v1/generate_deeplink_by_qr',
  sourceInfo: sourceInfo,
);

final deeplinkData = await _khqrSdk.generateDeepLink(deeplinkInfo);
```

### KHQR Card Widget
```dart
KhqrCardWidget(
  width: 300.0,
  receiverName: 'John Smith',
  amount: 0,
  currency: KhqrCurrency.khr,
  qr: khqrContent,
),
```

## Activities