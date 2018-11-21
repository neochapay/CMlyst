# CMlyst
CMlyst is a Content Management application built upon Cutelyst with support for Menus, Pages, Blogs and Feeds
 
 Help is welcome :)

## Dependencies
 * Grantlee
 * Cutelyst 2.0.0 with enablend Grantlee plugin

## Configuration
Create an INI file like cmlyst.conf with:

    [Cutelyst]
    DataLocation = /var/tmp/my_site_data
    production = true
    dbDriver = sqlite

Where:
 * DataLocation is the place where images uploads and sqlite database will be placed
 * production when true will preload the theme templates, which is a lot faster but if you are customizing the theme you will need to reload the process
 * dbDriver is SQL driver may be mysql or sqlite
 * dbServerHost host of data base (only for mysql)
 * dbServerBaseName name of data base (only for mysql)
 * dbServerUser user of data base (only for mysql)
 * dbServerPassword password of user database (only for mysql)
 * dbServerPort port of database (only for mysql)
 
## Running
You can run it with cutelyst-wsgi or uWSGI, both have similar command line options, and you should look at their documentation to know their options, the simplest one:

    cutelyst-wsgi --application path/to/libcmlyst.so --http-socket :3000 --ini cmlyst.conf --chdir parent_of_root_dir --static-map /static=root/static
    
The chdir needs to point to the parent of the root directory that came from this project. The option --static-map is used to serve the static files.
  
Now point your browser to http://localhost:3000/setup

## Setup
To create the first admin user set the SETUP enviroment variable, run the server and point your browser to http://localhost:3000/.admin.

## Paths
 * http://localhost:3000/.admin  Admin interface
 * http://localhost:3000/.feed RSS feed
 * http://localhost:3000/.author/slug Author page
 
