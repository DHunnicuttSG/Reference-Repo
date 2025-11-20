* Link to load go onto your EC2 instance  
  * wget https://go.dev/dl/go1.25.4.linux-amd64.tar.gz  

* Remove previous installs of go and extract current download
  * rm -rf /usr/local/go && tar -C /usr/local -xzf go1.25.4.linux-amd64.tar.gz  

* Add the path to your EC2 instance:  
  * export PATH=$PATH:/usr/local/go/bin
 
* Verify install  
  * go version
