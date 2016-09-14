## Android SDK

### Generate keystore

    keytool -exportcert -alias co.za.iriesoft.chatspace -keystore co.za.iriesoft.chatspace.keystore

### Get SHA-1 Fingerprint

    keytool -list -v -keystore co.za.iriesoft.chatspace.keystore -alias co.za.iriesoft.chatspace -storepass <password> -keypass <password>

