# learn-splunk-enterprise-universal-forwarder
How to upgrade
```
rpm -Uvh splunk-6.0.2-196940-linux-2.6-x86_64.rpm --relocate /opt=/mnt/XX/
```
How to install splunk enterprise and universal forwarder

```ruby
wget -O splunk-9.4.0-6b4ebe426ca6.x86_64.rpm "https://download.splunk.com/products/splunk/releases/9.4.0/linux/splunk-9.4.0-6b4ebe426ca6.x86_64.rpm"
rpm -i splunk-9.4.0-6b4ebe426ca6.x86_64.rpm

wget -O splunk-9.3.2-d8bb32809498.x86_64.rpm "https://download.splunk.com/products/splunk/releases/9.3.2/linux/splunk-9.3.2-d8bb32809498.x86_64.rpm"

wget -O splunk-9.1.2-b6b9c8185839.x86_64.rpm "https://download.splunk.com/products/splunk/releases/9.1.2/linux/splunk-9.1.2-b6b9c8185839.x86_64.rpm"
rpm -i splunk-9.1.2-b6b9c8185839.x86_64.rpm

wget -O splunkforwarder-9.1.2-b6b9c8185839.x86_64.rpm "https://download.splunk.com/products/universalforwarder/releases/9.1.2/linux/splunkforwarder-9.1.2-b6b9c8185839.x86_64.rpm"
rpm -i splunkforwarder-9.1.2-b6b9c8185839.x86_64.rpm

wget -O splunkforwarder-9.3.2-d8bb32809498-x64-release.msi "https://download.splunk.com/products/universalforwarder/releases/9.3.2/windows/splunkforwarder-9.3.2-d8bb32809498-x64-release.msi"

wget -O splunkforwarder-9.3.2-d8bb32809498.x86_64.rpm "https://download.splunk.com/products/universalforwarder/releases/9.3.2/linux/splunkforwarder-9.3.2-d8bb32809498.x86_64.rpm"
```

How to start
```ruby
cd /opt/splunkforwarder/bin
	./splunk start
	./splunk stop
	./splunk restart
	./splunk help
sudo ./splunk start --accept-license
sudo ./splunk enable boot-start
```
## Add this to install without credentials
```ruby
sudo ./splunk start --accept-license --no-prompt
IMPORTANT: Because an admin password was not provided, the admin user
 will not be created. You will have to set up an admin username/password
 later using user-seed.conf.
```
## How to enable port 9997
```ruby
sudo ./splunk enable listen 9997 -auth <username>:<cleartextpassword>
```
How to forward logs to HF/Index
```ruby
sudo ./splunk add forward-server X.X.X.X:9997
OR
sudo ./splunk add forward-server X.X.X.X:9997 -auth <username>:<cleartextpassword>
sudo ./splunk list forward-server
sudo ./splunk list monitor 
sudo ./splunk add monitor /var/log 
sudo ./splunk list monitor 
sudo ./splunk list forward-server
sudo ./splunk restart
sudo ./splunk list forward-server
```
## Resource
https://community.splunk.com/t5/Installation/Upgrade-Splunk-using-RPM/m-p/32018

https://docs.splunk.com/Documentation/Forwarder/9.2.1/Forwarder/Configuretheuniversalforwarder

https://docs.splunk.com/Documentation/Splunk/9.2.1/Installation/StartSplunkforthefirsttime

https://docs.splunk.com/Documentation/Splunk/7.3.1/Forwarding/Enableareceiver

https://community.splunk.com/t5/Installation/How-to-Retrieve-Splunk-admin-password/m-p/543865
