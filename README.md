# Otp Reader

OTP (One-Time Password)  Reader Library for Android helping easily implement listening of SMS messages and using the callback methods to perform password verification etc.

### Gradle Dependencies

> build.gradle (Project wide)
```
allprojects {
    repositories {
        jcenter()
        maven { url "http://dl.bintray.com/swarajsaaj/Contributions" }
    }
}
```

> build.gradle (module)
```
compile 'swarajsaaj:otpreader:1.0'
```

### Usage

To implement the Otp reader in the application:-

1. Implement the OTPListener Interface in your activity
2. Bind the current Activity (or OTPListener) to OtpReader with second argument as the sender number (e.g. if it might be like BM-BIZY, DM-BIZY or some constant like 9898982222 , enter any extract substring of the expected number here or leave it blank to read all incoming messages. If not left blank the numbers containing the string will be considered for listening).

```
OtpReader.bind(this,"SENDER_NUM_HERE");
```

Override the otpReceived method
```
  @Override
    public void otpReceived(String smsText) {
        //Do whatever you want to do with the text
        Toast.makeText(this,"Got "+smsText,Toast.LENGTH_LONG).show();
        Log.d("Otp",smsText);
    }
```

#### Thats it. otpReceived will be called when the message is received.