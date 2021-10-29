# Salus
Service availability scanner for CNIT 470: Incidence Response. Uses Discord webhooks for easy configuration.

![salus](https://cdn.discordapp.com/attachments/824827852763168808/903081864217129001/unknown.png)

Runs nmap to check the status of running services on several machines.
If a failure is detected (cannot reach host or service is down), a message is sent to a Discord channel with the following info:
* which hosts are still online
* which hosts have failed
* which services have failed

### Discbin Setup
Get Discbin here: https://github.com/thief-adj/discbin

Install jq:
>`sudo apt install jq -y`

Configure with:
>`chmod 770`

>`echo hello world | discbin [webhook url]`

A message should be sent by your webhook in its configured channel.

Note that discbin must have permission to write to itself. Also, consider adding discbin to your path.

### Salus Setup
Replace "00" in all IPs with your group number. For example, group 11:
>`sed -i s/.00./.11./g salus`

Also, edit the salus file's "discbin" variable to the full path to the discbin script. For example, if your user is "alice", and you downloaded to home:
>`discbin='/home/alice/discbin/discbin'`

Lastly, remove the private IP address of whichever machine is running Salus from the `hosts` and/or `servhosts` arrays.

### Running Scheduled, Automatic Scans:
Advisable to run this in a screen. Alternatively, you can use cron jobs or you can create a system service. Screen is the easiest, though.
>`screen`

You can use the watch command to run the salus scan every n seconds. For example, the below command will run every 5 minutes. 
>`watch -n 300 "sudo ./salus"`

Remember to detach from your screen with Ctrl + A, D.

Salus only sends messages on service failure, so you don't have to worry about being spammed. (Unless your services go down).
