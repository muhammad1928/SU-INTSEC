# SU INTSEC

### You can install TLDa(i) instead of commandline if you want

´´´bash
aa
´´´

## 1.0 run this command to get acces to the docker container supplied by the teacher 
`docker run -it nharrand/scavenger-hunt:latest /bin/bash`


## 1.1 generate a random secret number
`python3 generate_clues.py [secret_number]` "turorialDocker12"

The first command we are going to learn is `man`, which is short for manual. Typing `man [command]` will give you a help page (usually called a manpage) for most commands.

The next command we need to learn is `ls` (list). Type `man ls` and read the description. Press `q` to exit. Then type `ls` and you should see something like this:

## 2.0 clues
Weneed a couple more tools before we can start clue hunting. To change to another directory we use `cd` (change directory). You may notice that `man cd` doesn’t work. Sometimes there is no manpage for a command. In that case google is your friend. Changing directories is pretty simple: cd clues This puts us in the clues directory. To go up a directory, we can do this: cd .. If you ever get lost, just do cd ~/scavenger-hunt to return home. If you `cd` to the `clues` directory and do an `ls`, you will notice that there are a lot of clue directories. Most of them contain fake clues. Throughout our hunt we will be looking for real clues. Using `cd`, navigate to `clues/12345` and type `ls`. You should see a single file named `clue`.

## 2.1 Cat
Finally we need to be able to look at our clues. First read the manpage for `cat`, then do: cat clue This should list the clue in your terminal. From now on, everything we need will be contained in these clue files. It’s a good idea to keep track of all the clue folders (like `123456`) on a piece of paper. You can also do things like copy all the clue files to your home folder, or cut and paste the clue text into another file.cd


# Docker 
## 3.0 Starting a container
You already know that using `docker run` you can start a container based on an image. In this section, you will learn how to run, manage, and customize Docker containers. Follow each step carefully and experiment with the commands to understand how Docker works. At any time you can read the documentation of each of the commands mentioned during this lab. To get the list of docker commands run 'docker help' and to get more details on a specific command run 'docker [command]--help'.

-d = detached mode 
run this on background

`docker ps` will show me any containers running on my machine

`docker images` will show me the images that are downloaded in my machine

`docker ps -a ` will show all active and inactvie containers

`docker rm [container_name]` this will remove the stopped containrs.

`docker run -d -p 8080:80 --name my_httpd_container httpd` -p will connect docker port 8080 to our local machine port 8080:80

` docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' my_httpd_container` this will return the ip adress


## 3.1 Use docker exec to Open a Shell Inside the Container:
` docker exec -it my_httpd_container /bin/bash` this will enter the container and allow  you acces shell. 

navigate to `/usr/local/apache2/htdocs/` using `cd /usr/local/apache2/htdocs/`

then this is used to modify your webpage

`apt update` and `apt install nano` to be able to edit index.html

open index html file using `nano index.html`

`cat index.html` will show you the raw html file.