# Firebase Analytics

## Enabling DebugView

### Android

1. Have Android SDK and adb command line interface
2. To enable adb, put this in your .bash-profile: 

      ```
      export PATH=\~/Library/Android/sdk/tools:$PATH
      export PATH=~/Library/Android/sdk/platform-tools:$PATH
      ```
  
3. Open up an emulator from android studio
4. Run adb shell setprop debug.firebase.analytics.app com.boatsgroup.boatwizard
5. Run the app on your android emulator (whatever you choose)
6. To Disable: adb shell setprop debug.firebase.analytics.app .none

### iPhone

1. Open Xcode
2. Product -> Edit Scheme... -> Run -> Arguments
3. Add Argument: -FIRDebugEnabled
4. To Disable: -FIRDebugDisabled
