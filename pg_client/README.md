# Create a psql postgres tools docker image
And mount a host directory to hold the .psql_history and .psqlrc files.

This lets you 
* use the pg client tools almost seamlessly on a mac, 
* persist your psql history
* persist your psql configuration

## build the image
```
docker build -t simon/pg_client .
```

## create a new container,

Note - the directory you specify here should exist, and should hold your . files ( if they exist yet, otherwise they will be created here)


Create as many of these containers as you need - your . files will outlive the containers
```
docker run --name psql -v /Users/simond/.psql_container_dir:/root  -it  simon/pg_client /bin/ash
```



## run, and attach to the container

```
$ docker start psql; docker attach psql
```


## add a shortcut to run and attach to the psql container
```
echo "alias psql='docker start psql; docker attach psql'" >> ~/.bash_profile
```
