# SeismicDatallogger_Utils

Daily report message with the State of Health of a remote seismic station connected to internet by modem. Linux mailutils must be installed and configured.

- Certimus_Guralp/check_CertimusSOH.job

  Bash script to retireve SOH from a Certimus Guralp and send a daily email. Linux mailutils must be installed and configured.

  Ex: ./check_CertimusSOH.job YS EP05 80.66.245.191 >& ./Trash/YS_EP05.log &


- Taurus_Nanometics/check_TaurusSOH.job

  Bash script to retireve SOH from a Taurus Nanometrics and send a daily email. Linux mailutils must be installed and configured. Linux mailutils must be installed and configured.


  EX: ./check_TaurusSOH.job YS EP06 87.218.198.245 >& ./Trash/YS_EP06.log &
