kd is intended to make cd'ing easier

The script gets a close match to a directory from command line arguments then prints that to stdout which allows a usage in bash like

    $ cd $(python kd.py /usr local bin)
    $ cd $(python kd.py /bin/ls)

For convenience a bash function is also provided, which can be set up like

    $ source kd.sh

Then one can use "kd" as a replacement for cd

    $ cd /usr/local/lib/python2.7/site-packages
    $ kd /usr lo li py si

First argument is a directory, subsequent arguments are prefixes of sub-directories. For example:

    $ kd /usr/local bi
    /usr/local/bin

Or first argument is a file

    $ kd /bin/ls
    /bin

Or first argument is a stem of a directory/file. kd.py will add * on to such a stem, and will always find directories first, looking for files only if there are no such directories

    $ kd /bin/l
    /bin

If nothing matches then give directories in $PATH which have matching executables

    $ kd ls
    /bin
