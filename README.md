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

This application is written in Java, and requires it to be installed on your Operational System of choice. 
Please find more details [here](https://www.java.com/en/download/help/index_installing.html).

### Download 

Please download the latest version of this application (v1.0.0) [here](release-1.0.0.zip
). 

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

Open the file `application.properties` and edit the following lines replacing with the values from the previous steps.

```
oura.accessToken=[OURA_ACCESS_TOKEN]
intervals.athlete.id=[INTERVALSICU_ATHLETE_ID]
intervals.apikey=[INTERVALSICU_TOKEN]
```

If at any point your API Keys for Oura and/or intervals.icu are regenerated you will need to update the corresponding 
entries in this file. 

### Running the application

If you are on Windows, you can use the shortcut provided in `oura_intervals.bat` file. 

If you are on MacOS or *nix-based OS you can use `java -jar oura-intervals-integration.jar`.

### Further details

Once you execute the application for the first time it will pull all sleep data from Oura and upload to intervals.icu up
to the current day. At the end of the process a file will be created with the name `date-checkpoint.dat`. This file  
contains the last date that the data was uploaded, so it doesn't need to upload all the data on every execution.

After the first execution only the data between the last execution and the current date will be uploaded. 

In case of issues a log file named `application.log` can be found in the application directory and it provides further
detail and well keep history of the past executions. 

### Reporting issues

If you have any issue or suggestion to report, you can do so on the [Github page](https://github.com/neillfontes/oura-intervals-integration/issues).