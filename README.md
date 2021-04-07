# Oura Ring intervals.icu Integration

## Description

This application pulls data from [Oura Ring Cloud](https://cloud.ouraring.com/) and uploads it to [intervals.icu](https://intervals.icu/).

Please find below the table of correlation between the two platforms:

| Oura       | intervals.icu |
|------------|---------------|
| hr_average | restingHR     |
| total      | sleepSecs     |
| rmssd      | hrv           |

### References:
- [Oura Ring Cloud API Documentation](https://cloud.ouraring.com/docs/sleep)
- [intervals.icu API Documentation](https://forum.intervals.icu/t/api-access-to-intervals-icu/609)

## Installation

### Pre-requirements

This application is written in Java, and requires Java 11 to be installed on your Operational System of choice. 
Please find more details [here](https://adoptopenjdk.net/releases.html).

- [Windows](https://github.com/AdoptOpenJDK/openjdk11-binaries/releases/download/jdk-11.0.10%2B9/OpenJDK11U-jre_x64_windows_hotspot_11.0.10_9.msi)
- [MacOS](https://github.com/AdoptOpenJDK/openjdk11-binaries/releases/download/jdk-11.0.10%2B9/OpenJDK11U-jre_x64_mac_hotspot_11.0.10_9.pkg)

### Download 

Please download the latest version of this application (v1.0.0) [here](https://github.com/neillfontes/oura-intervals-integration/releases/download/v1.0.0/release-1.0.0.zip). 

### Generate Application Tokens

In order to pull the data from Oura Ring Cloud and upload it to intervals.icu two application tokens are necessary. Do 
not share this information with others otherwise they can access information from your accounts.

#### Oura Ring Cloud

A personal access token can be generated [here](https://cloud.ouraring.com/personal-access-tokens). Once you have 
generated it, copy it temporarily for later use.

#### intervals.icu

An API Key can be generated [here](https://intervals.icu/settings). Once you have
generated it, copy it temporarily for later use. Also make not of your Athlete ID because it will be required for 
setting up the integration.

### Setting it up 

Extract the zip file in a folder of your choice. 

Open the file `application.properties` and edit the following lines replacing with the values obtained from the previous steps.

```
oura.accessToken=[OURA_ACCESS_TOKEN]
intervals.athlete.id=[INTERVALSICU_ATHLETE_ID]
intervals.apikey=[INTERVALSICU_TOKEN]
```

If at any point your API Keys for Oura and/or intervals.icu are regenerated you will need to update the corresponding 
entries in this file. 

### Running the application

If you are on Windows, you can use the shortcut provided in `run-app.bat` file. 

If you are on MacOS or *nix-based OS you can use `java -jar oura-intervals-integration.jar` or the `run-app.sh` file. 

The application runs in the background, so it doesn't have any user interface. 

### Further details

Once you execute the application for the first time it will pull all sleep data from Oura and upload to intervals.icu up
to the current day. At the end of the process a file will be created with the name `date-checkpoint.dat`. This file  
contains the last date that the data was uploaded, so it doesn't need to upload all the data on every execution.

After the first execution only the data between the last execution and the current date will be uploaded. 

In case of issues a log file named `application.log` can be found in the application directory and it provides further
detail and well keep history of the past executions. 

### Reporting issues

If you have any issue or suggestion to report, you can send me an e-mail: `neillfontes [at] gmail [dot] com` 