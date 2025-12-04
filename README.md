# SeismicStations_SOH
Daily report message with the State of Healt of a seismic station

- check_CertimusSOH.job

Bash script to retireve SOH from a Certimus Guralp and send a daily email.

Ex: ./check_CertimusSOH.job YS EP05 80.66.245.191 >& ./Trash/YS_EP05.log &


- check_TaurusSOH.job

Bash script to retireve SOH from a Taurus Nanometrics and send a daily email.

EX: ./check_TaurusSOH.job YS EP06 87.218.198.245 >& ./Trash/YS_EP06.log &
