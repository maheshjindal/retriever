![Retriever logo](http://i.imgur.com/M5hhENV.png)  [![Build Status](https://travis-ci.org/weecology/retriever.png)](https://travis-ci.org/weecology/retriever)

Large quantities of ecological and environmental data are increasingly available thanks to initiatives sponsoring the collection of large-scale data and efforts to increase the publication of already collected datasets. As a result, progress in ecology is increasingly limited by the speed at which we can organize and analyze data. To help improve ecologists' ability to quickly access and analyze data we have been developing software that designs database structures for ecological datasets and then downloads the data, pre-processes it, and installs it into major database management systems (at the moment we support MySQL, PostgreSQL, SQLite, and Microsoft Access).

Once the EcoData Retriever has loaded the data into the database it is easy to connect to the database using standard tools (e.g., MS Access, Filemaker, etc.).The EcoData Retriever can download and install small datasets in seconds and large datasets in minutes. The program also cleans up known issues with the datasets and automatically restructures them into a format appropriate for standard database management systems. The automation of this process reduces the time for a user to get most large datasets up and running by hours, and in some cases days.

Installing (binaries)
---------------------

Precompiled binaries the most recent release are available for Windows, OS X,
and Ubuntu/Debian at the [project website](http://ecodataretriever.org).


Installing From Source
----------------------

To install the EcoData Retriever from source, you'll need Python 2.6 with the following packages installed:

* wxPython
* xlrd

###The following packages are optional

* PyMySQL or MySQLdb (for MySQL)
* sqlite3 (for SQLite)
* psycopg2 (for PostgreSQL)
* pyodbc (for MS Access - this option is only available on Windows)

###To install from source

1. Clone the repository
2. From the directory containing setup.py, run the following command: ``python setup.py install``
3. After installing, type ``retriever`` from a command prompt to launch the Database Toolkit,
   or find main.py in your Retriever directory and run it in Python.

Using the Command Line
----------------------
After installing, run `retriever update` to download all of the available dataset scripts. 
To see the full list of command line options and datasets run `retriever --help`. 
The output will look like this:
```
usage: retriever [-h] [-v] [-q] {install,update,gui,new,ls,citation,help} ...

positional arguments:
  {install,update,gui,new,ls,citation,help}
                        sub-command help
    install             download and install dataset
    update              download updated versions of scripts
    gui                 launch retriever in graphical mode
    new                 create a new sample retriever script
    ls                  display a list all available dataset scripts
    citation            view citation
    help

optional arguments:
  -h, --help            show this help message and exit
  -v, --version         show program's version number and exit
  -q, --quiet           suppress command-line output
```

To install datasets, use `retriever install`:

```
usage: retriever install [-h] [--compile] [--debug]
                         {mysql,postgres,sqlite,msaccess,csv} ...

positional arguments:
  {mysql,postgres,sqlite,msaccess,csv}
                        engine-specific help
    mysql               MySQL
    postgres            PostgreSQL
    sqlite              SQLite
    msaccess            Microsoft Access
    csv                 CSV

optional arguments:
  -h, --help            show this help message and exit
  --compile             force re-compile of script before downloading
  --debug               run in debug mode
```

For example, to install the Breeding Bird Survey data into an sqlite database named mydatabase.db you would use:

`retriever install sqlite BBS -f mydatabase.db`


Acknowledgments
---------------

Development of this software was funded by the [National Science Foundation](http://nsf.gov/) as part of a [CAREER award to Ethan White](http://nsf.gov/awardsearch/showAward.do?AwardNumber=0953694).
