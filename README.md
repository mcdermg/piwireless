# piwireless
Files for use on raspberry pi for placement in the boot sector for headless SSH and wireless network access.

The ssh file is empty and requires NO modification.#

The wpa_suppliciant.conf will need to be modified to allow access to a wireless network


Remove the following and replace it with your ISO-3166-1_two-letter_country_code: 
«your_ISO-3166-1_two-letter_country_code»

For your wireless network replace with your network details, SSID, psk (password) and you can specify key management (this may not be necessary but is good practice to specify.

    ssid="«your_SSID»"
    psk="«your_PSK»"
    key_mgmt=WPA-PSK

Be careful with passwords if commiting to source control. Yo can use wpa_passphrase command which pre-computes PSK entries for network configuration blocks of a wpa_supplicant.conf file. An ASCII passphrase and SSID are used to generate a 256-bit PSK

Use this command: wpa_passphrase [ssid-name] [password-name] 

*be sure to wrap the network and/or password in quotes if you have spaces in either.

This command will output out a new network object that looks like this and can be used in the template wpa supplicant file so that your password is not exposed:

network={
	ssid="testNetwork"
	#psk="testingPassword"
	psk=575827beef2c7dbdcf817a9cd0e6b96fb0fd3f54e2c0fbf24a38eb04fb7e9aa3
}
