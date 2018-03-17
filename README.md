# Anomaly
Sensor Health Report and Anomaly Detection

## Problem Definition
Data recorded from sensors are not always right. Many a times we get false values from sensors. It is very useful to know the health of each sensor for a city manager. We are also finding the patterns in false values, which can help in making better decisions.

Also Sometimes the sensor might be giving correct value but its not aligned to value that we expect maybe because of some sudden environmental variations or activities around the sensor.

## Analysis
We are taking raw data from sensors and finding all sensor which are completely 'not working'. Along with that, we are also looking for malfunctioning sensors along with its type that are as follows:

* **constant_value**: This contains binary value (1/0). 1 means the sensor is giving constant value for the last focus window
![constant](https://user-images.githubusercontent.com/25451752/37552712-67bc2b8a-29e0-11e8-88c9-e835f17e5e63.png)

* **outlier**: This will show the when there has been an outlier detected with Timestamp. This contains binary value (1/0)
![outliers](https://user-images.githubusercontent.com/25451752/37552654-a1c9e21e-29df-11e8-8141-83a51ff10e33.png)

* **spikes**: This contains binary value (1/0).This will show the when there has been an spike detected with Timestamp.
![spikes](https://user-images.githubusercontent.com/25451752/37552714-6bc421e2-29e0-11e8-87d3-d2c7c4f3a47c.png)

* **abnormal_var**: This contains binary value (True/False). True means the sensor value abnormal variance from the rest of the sids and from the past.  To calculate abnormal variance we need 7 time more data of hours_to_consider in the past 
![abnormalv](https://user-images.githubusercontent.com/25451752/37552718-761912b0-29e0-11e8-8dc8-027ef90020b8.png)

* **calibration**: This will contain 3 values i.e., 'High'/'Low'/'none'. 'none' means there is no calibration error and 'high' means that this sid is showing higher values most of the times with respect to other sids. It can also contain **'not_applicable'** if we have single SID. Calibration is a peer analysis which cannot be done on a single sensor.
![calibration](https://user-images.githubusercontent.com/25451752/37552717-73892eae-29e0-11e8-9f78-c628f4989cb9.png)

## Imputation
Now that we know how to find out the "not-working" and "malfunctioning" sensors, we filter out the "not-working" sensors and impute the values of "malfunctioning" sensors before forecasting.

![imputation](https://user-images.githubusercontent.com/25451752/37557096-8eb228b2-2a25-11e8-9ddb-2e9a4a947f62.png)

![results](https://user-images.githubusercontent.com/25451752/37557144-484b6428-2a26-11e8-999d-44ffdf27cee1.png)

