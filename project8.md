Created an Ubuntu Server 20.04 EC2 instance and named it Project-8-apache-lb, and opened TCP port 80 on Project-8-apache-lb by creating an Inbound Rule in Security Group

![1  configure http for the LB](https://user-images.githubusercontent.com/79456052/180401113-aa5e1be8-c5be-4544-8708-d4ed1fe3cba2.png)

Installed Apache Load Balancer on Project-8-apache-lb server and configured it to point traffic coming to LB to both Web Servers and made sure apache2 was up and running


![2  install apache on the load balancer and ensure its up and running](https://user-images.githubusercontent.com/79456052/180402045-f7ca17e5-fffc-43c8-b04b-80195c929680.png)

Configured load balancing using the command *sudo vi /etc/apache2/sites-available/000-default.conf*, and added the configuration in the 
documentation into the file

![3  configure load balancing](https://user-images.githubusercontent.com/79456052/180401883-3a007e89-da89-4840-acac-016fcf8738fc.png)

Verified that the configuration worked by accessing the Load Balancer's  public IP address from my browser:

![Screenshot 2022-07-22 at 09 58 50](https://user-images.githubusercontent.com/79456052/180403817-dd9bcbee-2564-4841-87fe-676b92ac0df5.png)


Opened the terminals for both Web Servers and ran the  command *sudo tail -f /var/log/httpd/access_log*  refreshed the browser page several times and made sure that both servers received 
HTTP GET requests from the LB – The new records appeared in each server’s log file.

![5  the terminal shows the number of HTTP GET requests from the LB](https://user-images.githubusercontent.com/79456052/180404305-5a3439c9-3c87-4ae0-9c66-6914b8267a7b.png)


Configured local DNS Names resolution by editing the /etc/hosts file, and adding 2 records into the file with Local IP address and arbitrary name for both Web Servers i.e web1 and web2

![ 6  configured local dns name resolution on the LB server by openening the vi-etc-host file and ](https://user-images.githubusercontent.com/79456052/180405961-b0bf933e-c479-4e89-9166-bd90fdb89de8.png)


I also updated the Load Balancer config file with the names instead of IP addresses.

![7  updated the lb config file with the names instead of the ip addressess](https://user-images.githubusercontent.com/79456052/180406449-62aa2d38-2f9b-4d5f-b055-3e5b79528bb6.png)

I curled the web servers from LB locally curl http://web1 or curl http://web2 – and it worked.

![8](https://user-images.githubusercontent.com/79456052/180406740-fd5cd148-061f-4bcd-9336-ce4e80df646b.png)






