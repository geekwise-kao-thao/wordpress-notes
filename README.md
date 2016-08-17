# wordpress-notes

# steps to open wordpress via commander line thru docker compose

### in the terminal line type:

- docker-machine rm default (removes virtual machine named: default)

### then 

- docker-machine create --driver hyperv default (hyperv is used for windows)

- docker-machine env default (syncs the local machine to the docker machine (virtual). docker-machine installs docker-compose)

### note: mv in terminal is a quick way to rename a file

- docker-compose up (downloads all the layers for the image, building a docker image to run in a container)

- docker-machine ip default (default is the name of the machine)

### note: when opening wordpress use 'localhost' for window and 192.168.99.100 for mac

###  in the terminal: cd to correct folder (eg.  docker-setup) then type docker-compose up (to open up wordpress again)
# 8-17-16
# this is to setup for wordpress html5
- create a workspace in cloud 9
- open up wordpress, creating a login (child-theme for login and password with geekwise.kao.thao@gmail.com as email)
- go to themes and search for html5blank, if not there, then search in google and download it.  after that, in wordpress admin browse it in the downloaded files on pc and activate it. then select it 
