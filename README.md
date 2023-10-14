Spurtcommerce with Docker Deployment

------------------------------------------------------------------------------

Requirements

To use Docker with Spurtcommerce, you should have docker and docker-compose installed on your system by running the following command..

Step: 1

$ sudo snap install docker

// Installs Docker Engine

Note: 	The web-ui Service in docker yaml is Configured in default port 80..
      	Incase if any service is running in port 80..(ex: apache or nginx) in Your local system..
	change the port configuration in the follow code in docker.yaml file
	
	....
	web-ui:
    	container_name: spurtcommerce-web-ui
   	 image: spurtcommerce/spurt-web-ui:4.8.2
    	depends_on:
      	- spurtcommerce-api
    	ports:
      	- "{your-port}":80
      	....

Step 2: Run This Command for docker deployment

$ sudo docker compose up

executes compose.yaml file,
Pulls api and Webpanel Docker Images
And Automatically Containerized, Ports are configured.

-----------------------------------------------------------------------

Step 4: Wait for few mins for application to setup... Then SpurtCommerce Is Ready On localhost:{your-port} or default localhost/(hostname)
