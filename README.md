# SeismicDatallogger_Utils


- ## Cube_CCube_Digos/BorrarDatos_CUBE.job

  When a Digos CUBE datalogger fills its internal memory, it no longer record anymore data. Recording 3Ch at 100 sps its internal 32Gb memory can last 280 days, it is 9 month aproximately. If it is attacched to a CCUBE sending data by seedlink we want it recording continously, so it is necessary to delete the old data.

  We launch this script with Linux root's cron:
  
  ```
  > crontab -l
  
  # m h  dom mon dow   command
  
  0 0 1 */6 * /home/ccube-admin/BorrarDatos_CUBE.job > /home/ccube-admin/log 2>&1
  ```

  
- ## Cube_CCube_Digos/Check_Net_CCUBE.job

  When the CCube loses its network connection, it never recovers. We check the connection every hour with a ping and,if we don't get a response, we restart it directly.

  We launch this script using Linux root's cron:

  ```
  > crontab -l
  
  # m h  dom mon dow   command
  
  0 * * * * /home/ccube-admin/Check_Net_CCUBE.job > /home/ccube-admin/log_net 2>&1
  ```



- ## Certimus_Guralp/check_CertimusSOH.job

  Bash script to retireve  State of Health (SOH) from a Certimus Guralp and send a daily email. We have daily report messages with the SOH of a remote seismic station connected to internet by GPRS modem. Linux *mailutils* must be installed and configured.
   

  Ex: ``./check_CertimusSOH.job YH EP02 80.xx.yyy.91 >& ./Trash/YH_EP02.log &``
<img width="908" height="229" alt="Captura desde 2025-12-05 10-43-06" src="https://github.com/user-attachments/assets/32304d3f-973d-446d-94ae-fad0d3e22285" />

- ## Certimus_Guralp/Clean_Certimus_status.job
- ## Certimus_Guralp/Clean_Certimus_SOH.L.job

  Bash scripts to clean Certimus Status information (from MicroSD and seedlink) and obtain a simplified SOH file.

- ## Taurus_Nanometics/check_TaurusSOH.job

  Bash script to retireve SOH from a Taurus Nanometrics and send a daily email. We have daily report messages with the SOH of a remote seismic station connected to internet by GPRS modem. Linux *mailutils* must be installed and configured.


  EX: ``./check_TaurusSOH.job YH EP21 87.xxx.yyy.245 >& ./Trash/YH_EP21.log &``
<img width="845" height="219" alt="Captura desde 2025-12-05 10-41-58" src="https://github.com/user-attachments/assets/19ae7e25-74c1-4a24-b6cf-ba4ff3109be1" />

- ## SpiderNano_Worldsensing/Spider_PseudoTiempoReal_Geospace.job
  ## SpiderNano_Worldsensing/Spider_PseudoTiempoReal_TC.job

  Bash scipts to retieve the internal data of a SpiderNano Worldsensing (spd files), convert them to mssed and simulate a seedlink connection. It uses Worldsensing's tool *spd2ms* to obtain the mseeds files, Iris *Rinserver* (https://github.com/EarthScope/ringserver) to create a seedling rinbuffer and *qmerge* to split the mseed files. The scrip also sends a daily email with the SOH of the station. Linux *mailutils* must be installed and configured. The only diference between these two scripts is the correction of Geospace's polarity inversion:

```
195,196c193
< ##### ATENCION SPIDER CON GEOSPACE --> POLARIDAD INVERTIDA FLAG -p123 ACTIVADO !
<        spd2ms -s -n $NET -l " " -p123 -d new -o mseed
---
>        spd2ms -s -n $NET -l " " -d new -o mseed
```

```
Ex:
./Spider_PseudoTiempoReal_Geospace.job YY TIAN 108.147.138.195:8080 >& /home/eworm/RingServer/Logs/Descarga_TIAN.log &
./Spider_PseudoTiempoReal_TC.job FB FIJA 193.177.155.133:80 >& /home/eworm/RingServer/Logs/Descarga_FIJA.log &
```


