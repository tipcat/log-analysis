
## Log Analysis

### Use
_Log Analysis_ is a Python application that works in conjunction with SQL to deliver statistics on historical database use. The database belongs to a newspaper and contains the names of various articles and the authors who wrote them, logging each "hit" along with the date and time of user access. Running the application will display results on the following queries:

1. What are the 3 most popular articles of all time?
2. Who are the most read authors?
3. On which dates did user actions result in an error rate of 1% or greater?

### What You Need
_Log Analysis_ runs on a virtual Ubuntu box and utilizes the postgresql implementation of SQL. To get started please proceed as follows:

* You will need a shell window. If you're on a Mac this is the command line utility. If on Windows 7 or later you will need to download [Git BASH](https://gitforwindows.org/).

* In the shell you will run the Ubuntu box using [Vagrant](https://www.vagrantup.com/) in conjunction with [Virtual Box 5.2](https://www.virtualbox.org/wiki/Download_Old_Builds_5_2). **NOTE**: You cannot yet use VirtualBox 6 with Vagrant.

* Assuming you have installed those two components, download and unzip this file: [FSND-Virtual-Machine.zip](https://s3.amazonaws.com/video.udacity-data.com/topher/2018/April/5acfbfa3_fsnd-virtual-machine/fsnd-virtual-machine.zip) or fork and clone the Github [repository](https://github.com/udacity/fullstack-nanodegree-vm). This will give you a Vagrant box preconfigured with the postgresql package.

* Once you've done that, you will need to obtain the actual data file [newsdata.sql](https://d17h27t6h515a5.cloudfront.net/topher/2016/August/57b5f748_newsdata/newsdata.zip). Put the unzipped ``newsdata.sql`` file inside the ``vagrant`` subdirectory of your ``FSND-Virtual-Machine`` folder. This is **also** where you will place the ``log-analysis.py`` file which runs the application.

### Prepping the Database

Now it's time to ``vagrant up`` and then ``vagrant ssh`` into your virtual machine. Type ``cd /vagrant`` to access your shared files, which is where ``newsdata.sql`` and ``log-analysis.py`` will be.

Type ``psql -d news -f newsdata.sql`` to create the database tables and populate them with data. You can proceed to explore the database by typing ``psql -d news``. Use ``\dt`` to display the tables and ``\d table`` (replacing "table" with the name of a table) to navigate the table schema. You can also execute SQL commands from the ``news=>>`` prompt. The command will execute only when the ending semicolon ``;`` is reached, so longer queries may be broken up into smaller ones simply by hitting return.

### Running the Application

If you are still in the ``psql news=>`` prompt, type ``^ d`` to escape, which will bring you back to
the shared directory prompt ``/vagrant$``. You are ready to rock!

This application **must** be run in Python 3 to display the results in a readable format. The code does not rely on SQL views. Simply type ``python3 log-analysis.py`` while in the vagrant directory to run.

The application will take around 20 seconds to run, so please be patient while waiting for the results!
