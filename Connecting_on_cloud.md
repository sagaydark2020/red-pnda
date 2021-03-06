# Connecting to your instance on the cloud

If you're using EC2 or any other cloud provider as a means to test out red-pnda, then the chances are you might not be able to connect to the PNDA console through an elastic IP.

Here are the steps to overcome this limitation:

* ssh to your cloud instance with the '-D' and '-q' flags 
* '-q' sets the logging to quiet and suppresses any error messages
       
        ssh -i /path/to/your/key.pem -q -D 8888 ubuntu@54.x.x.x 
        
* Download FoxyProxy extension for your browser. Please use the following links to download

	[Chrome](https://chrome.google.com/webstore/detail/foxyproxy-standard/gcknhkkoolaabfmlnjonogaaifnjlfnp?hl=en)
	
	[Firefox](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/)
	
* Click on the FoxyProxy Icon, you should see this window

	<img src="images/foxyproxy_1.png" alt="FoxyProxy" width="300" height="200"/>

Then click on the first selection and then click on 'Edit Selection'
	
* Configure the FoxyProxy extension to look like this:

<img src="images/foxyproxy.png" alt="FoxyProxy" width="400" height="300"/>

Click 'OK'. Make sure the extension is enabled, you should see a blue indicator to the right of your address bar!

* Type the private IP of your cloud instance in the browser and you should see the PNDA console up and running!
* Magic!

## Security Group setting

For reference, here is the correct incoming firewall/security group settings for cloud-hosted instances. 

Type                | Protocol         | Port Range            | Source         |
--------------------|------------------|-----------------------|----------------
Custom TCP Rule     | TCP              | 3123                  | 0.0.0.0/0
Custom TCP Rule     | TCP              | 3123                  | ::/0
HTTP                | TCP              | 80                    | 0.0.0.0/0
HTTP                | TCP              | 80                    | ::/0
Custom TCP Rule     | TCP              | 9000                  | 0.0.0.0/0
Custom TCP Rule     | TCP              | 9000                  | ::/0
Custom TCP Rule     | TCP              | 8080                  | 0.0.0.0/0
Custom TCP Rule     | TCP              | 8080                  | ::/0
SSH                 | TCP              | 22                    | 0.0.0.0/0
SSH                 | TCP              | 22                    | ::/0
Custom TCP Rule     | TCP              | 4242                  | 0.0.0.0/0
Custom TCP Rule     | TCP              | 4242                  | ::/0
Custom TCP Rule     | TCP              | 3000-3001             | 0.0.0.0/0
Custom TCP Rule     | TCP              | 3000-3001             | ::/0
Custom TCP Rule     | TCP              | 10900                 | 0.0.0.0/0
Custom TCP Rule     | TCP              | 10900                 | ::/0
Custom TCP Rule     | TCP              | 9092                  | 0.0.0.0/0
Custom TCP Rule     | TCP              | 9092                  | ::/0