# salus
CNIT 470 incident response service scanner. Sends failures to Discord using discbin.
Uses nmap to check the status of running services on several machines.
If a failure is detected (cannot reach host or service is down), a message is sent to a discord channel with the following info:
* which hosts are still online
* which hosts have failed
* which services have failed

### Discbin Setup
Get Discbin here: https://github.com/thief-adj/discbin

Configure with:
>`chmod 770`
>`echo hello world | discbin [webhook url]`

### Run scan every 5 minutes (300s):

>`screen`

>`watch -n 300 "sudo ./salus"`
