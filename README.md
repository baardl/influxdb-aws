<h1 align="center">InfluxDB</h1>
<p align="center">
  <b>InfluxDB</b> is an open-source, distributed, time series database with no external dependencies.  
</p>

Current versions:
* Influxdb: 1.3.1
* Chronograph: 1.3.5

`Warning!`
Current implementation requires health chenck on Chronograph, not on the IfluxDb.
You will have to install Chronograph to make this setup work. [See Chronograph] (#Install-Chronograph)

## AWS Setup

#### Notes
This is not an HA setup, that requires clustering which this template doesn't include.  Clustering is not stable in the current release of Influxdb, for that reason, this template will focus on a single instance.

### Install
Upload the Influxdb template.  This will require a valid configuration file for Influxdb, it will replace the default config installed by the Influxdb RPM.  

There is a example config included in this repo.  

This template will create 2 EBS volumes, the first will become the root device for the database, the second will be a small device for the WAL.

## Authentiacation and Authorization

### Admin user

Create the first admin user
```
curl -XPOST http://<hostname>:8086/query --data-urlencode "q=CREATE USER <username> WITH PASSWORD '<pwd>' WITH ALL PRIVILEGES"
```



## Configuration
```
 sudo vi /etc/influxdb/influxdb.conf
 ```
## Management interface

From version 1.3 of InfluxDb you will have to install Chronograph to do administration. Script for this will follow...

### Install-Chronograph
For now do this:

ssh to your host
```
wget https://dl.influxdata.com/chronograf/releases/chronograf-1.3.5.0.x86_64.rpm
sudo yum localinstall chronograf-1.3.5.0.x86_64.rpm
```
#### Verify
http://hostname/
