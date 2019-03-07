# Check MDM
Checks the enrollment status of MDM on a Mac and reports it to **[Watchman Monitoring](https://www.watchmanmonitoring.com)**.

_\_check\_mdm.plist_ is a plist file to define the plugin for Watchman Monitoring. It contains optional settings to configure how the plugin will alert Watchman Monitoring.

_\_check\_mdm.plugin_ is a python script that, by default, will exit 0 if MDM is enrolled and user-approved, exit with a one-time alert if MDM isn't enrolled, and exit with continuous alerts if enrolled in an MDM but isn't user approved.

After installing and running for the first time the alert settings can be configured in System Preferences -> Monitoring Client -> Settings -> Check MDM.

Alternatively the settings can be configured with the CLI `defaults` command:

	sudo defaults write /Library/MonitoringClient/PluginSupport/_check_mdm_settings.plist KEY -int N

There are two keys:

* **mdm_warning**: which configures the MDM enrollment alert.
* **uamdm_warning**: which configures the MDM user approval alert.

Both keys take the following integer values: 0 == None, 1 == Warn, 2 == Alert.

* **None**: will only show an alert in Watchman Monitoring.
* **Warn**: will show an alert and Watchman Monitoring will email once.
* **Alert**: will show an alert and Watchman Monitoring will continuously email alerts.