# SeismicDatallogger_Utils


- ## Cube_CCube_Digos/BorrarDatos_CUBE.job

  When a Digos CUBE datalogger fills its internal memory, it no longer record anymore data. Recording 3Ch at 100 sps its internal 32Gb memory can last 280 days, it is 9 month aproximately. If it is attacched to a CCUBE sending data by seedlink we want it recording continously, so it is necessary to delete the old data.

  We use this script with Linux cron:
  
  ```
  > crontab -l
  
  # m h  dom mon dow   command
  
  0 0 1 */6 * /home/ccube-admin/BorrarDatos_CUBE.job > /home/ccube-admin/log 2>&1
  ```

  
- ## Cube_CCube_Digos/Check_Net_CCUBE.job

  When the CCube loses its network connection, it never recovers. We check the connection every hour with a ping and,if we don't get a response, we restart it directly.

  We use this script with Linux cron:

  ```
  > crontab -l
  
  # m h  dom mon dow   command
  
  0 * * * * /home/ccube-admin/Check_Net_CCUBE.job > /home/ccube-admin/log_net 2>&1
  ```



- ## Certimus_Guralp/check_CertimusSOH.job

  Bash script to retireve  State of Health (SOH) from a Certimus Guralp and send a daily email. We have daily report messages with the SOH of a remote seismic station connected to internet by GPRS modem. Linux mailutils must be installed and configured.
   

  Ex: ``./check_CertimusSOH.job YH EP02 80.xx.yyy.91 >& ./Trash/YH_EP02.log &``
<img width="908" height="229" alt="Captura desde 2025-12-05 10-43-06" src="https://github.com/user-attachments/assets/32304d3f-973d-446d-94ae-fad0d3e22285" />


- ## Taurus_Nanometics/check_TaurusSOH.job

  Bash script to retireve SOH from a Taurus Nanometrics and send a daily email. We have daily report messages with the SOH of a remote seismic station connected to internet by GPRS modem. Linux mailutils must be installed and configured. Linux mailutils must be installed and configured.


  EX: ``./check_TaurusSOH.job YH EP21 87.xxx.yyy.245 >& ./Trash/YH_EP21.log &``
<img width="845" height="219" alt="Captura desde 2025-12-05 10-41-58" src="https://github.com/user-attachments/assets/19ae7e25-74c1-4a24-b6cf-ba4ff3109be1" />
