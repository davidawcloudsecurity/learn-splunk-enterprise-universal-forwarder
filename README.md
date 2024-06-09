# learn-splunk-enterprise-universal-forwarder
How to install splunk enterprise and universal forwarder

```ruby
wget -O splunk-9.1.2-b6b9c8185839.x86_64.rpm "https://download.splunk.com/products/splunk/releases/9.1.2/linux/splunk-9.1.2-b6b9c8185839.x86_64.rpm"
rpm -i splunk-9.1.2-b6b9c8185839.x86_64.rpm

wget -O splunkforwarder-9.1.2-b6b9c8185839.x86_64.rpm "https://download.splunk.com/products/universalforwarder/releases/9.1.2/linux/splunkforwarder-9.1.2-b6b9c8185839.x86_64.rpm"
rpm -i splunkforwarder-9.1.2-b6b9c8185839.x86_64.rpm
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
https://docs.splunk.com/Documentation/Forwarder/9.2.1/Forwarder/Configuretheuniversalforwarder

https://docs.splunk.com/Documentation/Splunk/9.2.1/Installation/StartSplunkforthefirsttime
