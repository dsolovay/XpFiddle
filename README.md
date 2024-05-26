# XpFiddle
Generate demo Sitecore environments.

## Goal
Create a YML standard for specifying a Sitecore XM or XP Docker environment, including customizations to configuration or the SampleLayout.aspx file. This intended for use in contexts like Sitecore StackExchange or for bug reports. 

## Architecture
* YML format, including version specfifier (for allowing new features to be added.)
* PowerShell module that converts the YML file into a Docker-Compose environment.
* Optional config file that allows specifying user preferences such as Sitecore version, ltsc2019 vs ltsc2022, license location, etc.
* Output would be confined to static files that can be reviewed before being brough on line.

## Example

```yml
XpFiddleVersion: 0.1
base: xp0
modifications:
 - file: .\layouts\Sample Sublayout.aspx
   action: append
   content: |
    <p>Hello from XpFiddle!</p>
    <p>Running on machine <%= System.Environment.MachineName %>.</p>
```
would create a compose environment where this would be displayed after `docker compose up -d`:

![image](https://github.com/dsolovay/XpFiddle/assets/689532/8af18762-e484-4a31-9364-86be8f921c5e)

