# ������ Fun Home Assistant ���

## ���뷽ʽ

1. ��·�����Զ���������DNS�ٳ֣����������֣�������***apn2.airnut.com***ָ���Լ���Home Assistant������ַ�������ҵ���***10.0.0.105***�����巽����������������
2. ��[Easylink app](https://www.mxchip.com/easylink/)���Ӻ�WiFi��(���������̵Ƽ����ӳɹ�)��˫���˳�WiFi����ģʽ��
3. ͨ��hacs��װ�����߸����ļ���custom_components
4. ������������

```
#����Ǳ����е�
airnut:
  #ҹ���Ƿ����
  is_night_update: False
  #ҹ�俪ʼʱ��
  night_start_hour: 0001-01-01 23:00:00
  #ҹ�����ʱ��
  night_end_hour: 0001-01-01 06:00:00
 #�������д���
  weathe_code: 101280800
  
#ipΪ������������ip��ַ��������1s���������ݣ��ֱ�д�ĸ����͵Ĵ�����
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

#����еڶ���������������������������Դ�����
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
#����ĳ�������������Ҫ�ĳ������ڵĳ��д���
#�����뵽����Ѱ��
https://help.bj.cn/Weathera/20200304/320AD84ECBB0C14FBCF3518941E56179.html
http://api.help.bj.cn/api/CityCode.XLS
#����ÿ��10���Ӹ���һ�Σ���ν��ʤ����

## ����
��Ҳ���޸ĵģ�û�������ϵ������������ͻ�������

���лл֮ǰдairnut 1s�Ĵ��У�[ԭ����ַ](https://github.com/billhu1996/Airnut/)


