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



LETS FIND THE FLAGS inside `docker run-it nharrand/scavenger-hunt:latest /bin/bash`

lets start with creating a python clue using `python3 generate_clues.py [secret_number]` secret number is = 443323

## clue number one is `man`
man  is  the  system's  manual pager.  Each page argument given to man is normally the name of a program,   
utility or function.  The manual page associated with each of these arguments  is  then  found  and  dis-   
played.  A section, if provided, will direct man to look only in that section of the manual.  The default   
action is to search in all of the available sections following a pre-defined order (see DEFAULTS), and to   
show only the first page found, even if page exists in several sections.

*1*   Executable programs or shell commands
*2*   System calls (functions provided by the kernel)
*3*   Library calls (functions within program libraries)
*4*   Special files (usually found in /dev)
*5*   File formats and conventions, e.g. /etc/passwd
*6*   Games
*7*   Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7), man-pages(7)
*8*   System administration commands (usually only for root)
*9*   Kernel routines [Non standard]

``man ls`` Display the manual page for the item (program) ls.

``man man.7`` Display the manual page for macro package man from section 7.  (This is an  alternative  spelling  of "man 7 man".)

``bash man 'man(7)'`` Display  the manual page for macro package man from section 7.  (This is another alternative spelling of "man 7 man".  It may be more convenient when copying and pasting cross-references to manual pages.
Note that the parentheses must normally be quoted to protect them from the shell.)

``man -a intro``
    Display,  in  succession, all of the available intro manual pages contained within the manual.  It is
    possible to quit between successive displays or skip any of them.

``man -t bash | lpr -Pps``
    Format the manual page for bash into the default troff or groff format and pipe  it  to  the  printer
    named  ps.  The default output for groff is usually PostScript.  man --help should advise as to which
    processor is bound to the -t option.

``man -l -Tdvi ./foo.1x.gz > ./foo.1x.dvi``
    This command will decompress and format the nroff source manual page ./foo.1x.gz into a device  inde-
    pendent (dvi) file.  The redirection is necessary as the -T flag causes output to be directed to std-
    out with no pager.  The output could be viewed with a program such as xdvi or further processed  into
    PostScript using a program such as dvips.

``man -k printf``
    Search  the  short  descriptions  and manual page names for the keyword printf as regular expression.
    Print out any matches.  Equivalent to apropos printf.

``man -f smail``
    Lookup the manual pages referenced by smail and print  out  the  short  descriptions  of  any  found.
    Equivalent to whatis smail.
