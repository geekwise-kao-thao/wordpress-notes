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
- go to themes and search for html5blank-stable, if not there, then search in google and download it.  after that, in wordpress admin browse it in the downloaded files on pc and activate it. then select it
- in cloud 9, create a child theme by creating a folder in the same directory as the html5blank-stable folder (for eg. if the html5blank-stable folder is in the themes folder, then you must create the html5blank-stable-child folder)
- then in the html5blank-stable-child folder, create a file and name it style.css and open it to view it
- add this comment to the new style.css file:
```
	/*
	Theme Name: HTML5 Blank Child Theme
	Theme URI: https://child-theme-geekwise-kao-thao.c9users.io/
	Template: html5blank-stable
	Description: An Awesome HTML5 Blank WordPress Child Theme
	Author: Kao Thao (@kausthoj)
	Version: 0.1.0
	*/
```
- theme name is the new child theme name
- theme uri is where it is
- template is the parent theme (in this case it's the html5blank-stable theme)
- description is a brief explanation of the child theme
- author is you
- version is a number given to your theme

- to get all the css from the parent theme, you must import it using this:  @import url("../html5blank-stable/style.css");
- however, for this particular parent theme, it is not child friendly per stackoverflow.  to resolve the issue, you must create a new file called functions.php in the new child theme and add this new code in it:

```
<?php
    // De-register HTML5 Blank styles
    function html5blank_styles_make_child_active()
    {
    wp_deregister_style('html5blank'); // Enqueue it!
    }
    add_action('wp_enqueue_scripts', 'html5blank_styles_make_child_active', 100); // Add Theme Child Stylesheet

    // Load HTML5 Blank Child styles
    function html5blank_styles_child()
    {
    wp_register_style('html5blank-child', get_stylesheet_directory_uri() . '/style.css', array(), '1.0', 'all');
    wp_enqueue_style('html5blank-child'); // Enqueue it!
    }
    add_action('wp_enqueue_scripts', 'html5blank_styles_child'); // Add Theme Child Stylesheet
    ?>
```

- please see stackoverflow instructions: <http://stackoverflow.com/questions/25289973/creating-a-child-theme-for-html5-blank>
- test your new style.css file in the child theme folder by changing the background color to the body.
