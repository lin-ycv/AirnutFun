# 空气果 AirNut Fun Home Assistant Integration

## Setup

1. DNS override to point ***apn2.airnut.com*** to your Home Assistant local IP，ie: ***10.0.0.10***
2. Use [Easylink app](easylink_v3.2.apk) to configure AirNut to connect to your wifi, double click button after setup in app
3. Add `custom_components\airnut` to `\config` folder on HA (samba/ssh/file editor)
4. Configure as below
###
1. whether to update during the night or not `is_night_update: False`
2. `is_night_update=true` means 24 hours loging, `is_night_update=false` pauses during the night; set `night_start_hour` to `00:00:00` to disable loging
3. `SCAN_INTERVAL` configures how often loging is done, `= datetime.timedelta(seconds=600)`  is equivalent to 10 min (default)
4. to keep screen constantly on, interval can be set to 1 min (loging pm2.5 takes 1~2 mins)

configuration.yaml
```yaml
# Required
airnut:
  is_night_update: False
  # choose ONE
  night_start_hour: 0001-01-01 23:00:00
  night_start_hour: 0001-01-01 0:00:00
  night_end_hour: 0001-01-01 06:00:00
  # City code (Taipei)
  weathe_code: 101340101

homeassistant:
  unit_system: metric
  customize: !include customize.yaml

# local ip of airnut fun, each device have 4 sensors
sensor:
  - platform: airnut
    ip: "10.0.0.105"
    type: temperature
  - platform: airnut
    ip: "10.0.0.105"
    type: humidity
  - platform: airnut
    ip: "10.0.0.105"
    type: pm25
  - platform: airnut
    ip: "10.0.0.105"
    type: battery
  - platform: airnut
    ip: "10.0.0.105"
    type: weathe

# if you're using more than one device, add accordingly
  - platform: airnut
    ip: "10.0.0.xxx"
    type: temperature
  - platform: airnut
    ip: "10.0.0.xxx"
    type: humidity
  - platform: airnut
    ip: "10.0.0.xxx"
    type: pm25
  - platform: airnut
    ip: "10.0.0.xxx"
    type: battery
  - platform: airnut
    ip: "10.0.0.xxx"
    type: weathe
```

customize.yaml
```yaml
# Set icon and name
sensor.airnut_fun_pm25:
  icon: mdi:blur
  friendly_name: PM2.5
sensor.airnut_fun_battery:
  icon: mdi:battery
  friendly_name: Battery
sensor.airnut_fun_temperature:
  icon: mdi:thermometer
  friendly_name: Temperature
sensor.airnut_fun_humidity:
  icon: mdi:water-percent
  friendly_name: Humidity
sensor.airnut_fun_weathe:
  icon: mdi:weather-windy
  friendly_name: Weather
  
```
## Change city code to match yours
## code can be found here (in the url once you select a city)
https://www.qweather.com/
## updates every `SCAN_INTERVAL` seconds (default: 10min)

# 如果遇到时间不准确，或者是utc时间，请看下面
## 找到项目里面的_init_.py文件，找到下面
## def get_time_unix():
##     return int((datetime.datetime.now() + datetime.timedelta(hours=8)).timestamp())
## 改成
##  return int((datetime.datetime.now() + datetime.timedelta(hours=8)).timestamp())
## 或者
##  return int((datetime.datetime.utcnow() + datetime.timedelta(hours=8)).timestamp())
## 请自行测试那一条适用，导致这个原因是docker环境或者主机环境时区问题影响,每个设备不能同时照顾


