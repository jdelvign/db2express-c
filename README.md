# **db2express-c v11.1**
db2express-c V11.1 resources to build DB2 express-c image.

## Build the `db2express-c` image
Download the db2express-c v11.1 package for linux from IBM website(**v11.1_linuxx64_expc.tar.gz**) and copy it into the `db2express-c` directory

Create the db2data volume that hold the data for the db2inst1 instance :

    docker volume create db2data

`cd` into `db2express-c` directory

Launch the image build, take a look at the [Dockerfile](./db2express-c/Dockerfile) :

    ./build.sh 

Once the build is done and no major error happens, you can run the container :

>At Build time, there is actually no way to set the IPC option with the `docker build` command so at the end of the installation db2start do nothing and end with a SQL Error but the installation ends with a exit code 0

    ./db2start.sh

Now you can create database and do want you want, DB2 is alive, ALIVE !

To connect to the running container, you can use :

    ./bash.sh

Check the logs, it come from the tail -F db2diag.log into the [entrypoint.sh](./db2express-c/entrypoint.sh)

    docker logs -f db2