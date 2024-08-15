# rofi-pass-modi

[Rofi](https://github.com/DaveDavenport/rofi) modi to copy passwords to clipboard from [Unix pass](https://www.passwordstore.org/) password store.

This is a fork from [this script](https://github.com/RoshBeed/rofi-pass-modi/) which was updated to include fields management. It functions in a hybrid dmenu mode: it is first run without dmenu mode but then switches to dmenu mode. The objective is to avoid conflicts between potential passwords request windows and the rofi menu.

## Usage
Pass arguments through command line
```
rofi -show pass -modi pass:./rofi-pass-modi
```
or append to ```.config/rofi/config```
```
rofi.modi: 	pass:/<dir-to-rofi-pass-modi>/rofi-pass-modi
```
## Why rofi-pass-modi ?

Compared to the [previous version](https://github.com/RoshBeed/rofi-pass-modi/) of the script the following features have been added:
- management of fields in the format `field name: content`;
- solved an issue which often freezes the menu when a password was requested (e.g. from pinentry).

Compared to [autopass.cr](https://gitlab.com/repomaa/autopass.cr) and the unmaintained [rofi-pass](https://github.com/carnager/rofi-pass) this script has much less features. However it has one advantage: it can, and should, be used as a standard rofi modi and thus integrated in your standard rofi menu without being called independently.

## Password file format

The files must have the password as the first entry and each entry in a row with title separated from content by a ':'. OTP are handled by pass-otp. Here is an example:
```
mywonderfullpass
username: boby
url: htps://awebsite.com
otpauth://totp/Example:alice@google.com?secret=JBSWY3DPEHPK3PXP&issuer=Example
other: whatever you want
```

Multiline fields are not supported.

## Dependencies

- [pass](http://www.passwordstore.org/)
- [pass-otp](https://github.com/tadfisher/pass-otp) (optional: for OTPs)
- [rofi](https://github.com/DaveDavenport/rofi)
