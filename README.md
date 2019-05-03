# home-assistant-custom-components

Some of my custom components for home-assistant. <http://www.home-assistant.io>

Component Overview
------------------
  * [Local Tuya](#local-tuya)

## Local Tuya

NOTE: This component is beta version.

More information about used components can be found here:

- <https://github.com/codetheweb/tuyapi> by codetheweb and blackrozes
- <https://github.com/clach04/python-tuya> by clach04 

This component control the Tuya Switch 

### Installation

- Copy directory `local_tuya` to your `<config dir>/custom_components` directory.
- Configure with config below.
- Restart Home-Assistant.

### Usage
To use this component in your installation, add the following to your `configuration.yaml` file:

```yaml
# Example configuration.yaml entry

switch:
  - platform: local_tuya
    host: IP_ADDRESS
    local_key: LOCAL_KEY
    device_id: DEVICE_ID
    name: "Device Name"
    
```

Configuration variables:

- **name** (*Optional*): Name of the device.
- **host** (*Required*): The hostname or IP address on which the Switch can be reached.
- **local_key** (*Required*): The Local Key of switch [How-to](#Linking-a-Tuya-Device)
- **device_id** (*Required*): The Device Id [How-to](#Linking-a-Tuya-Device)


### Screenshot
![alt text](https://github.com/adrianoamalfi/home-assistant-custom-components/raw/master/screenshoots/local_tuya.PNG "Screenshot")


### Get the local_key & device_id
#### Linking a Tuya Device

1. Add any devices you want to use with `tuyapi` to the Tuya Smart app.

2. Install the CLI tool by running `npm i @tuyapi/cli -g`. If it returns an error, you may need to prefix the command with `sudo`. (Tip: using `sudo` to install global packages is not considered best practice. See [this NPM article](https://docs.npmjs.com/getting-started/fixing-npm-permissions) for some help.)

3. Install AnyProxy by running `npm i anyproxy -g`.  Then run `anyproxy-ca`.

4. Run `tuya-cli list-app`.  It will print out a QR code; scan it with your phone and install the root certificate.  After installation, [trust the installed root certificate](https://support.apple.com/en-nz/HT204477).

5. [Configure the proxy](http://www.iphonehacks.com/2017/02/how-to-configure-use-proxy-iphone-ipad.html) on your phone with the parameters provided in the console.

6. Enable full trust of certificate by going to Settings > General > About > Certificate Trust Settings

7. Open Tuya Smart and refresh the list of devices by "pulling down".

8. A list of ID and key pairs should appear in the console.

9. It's recommended to untrust the root certificate after you're done for security purposes.

#### Note

* Only one TCP connection can be in use with a device at once. If using this, do not have the app on your phone open.
* Some devices ship with older firmware that may not work with tuyapi. If you're experiencing issues, please try updating the device's firmware in the official app.


## Related Projects:
https://github.com/codetheweb/tuyapi 
https://github.com/clach04/python-tuya

