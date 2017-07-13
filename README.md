# DOCKER FILES

## jenkins-sencha-cmd

Includes:

    - jenkins
    - jenkins plugins
        + git plugin
    - Sencha Cmd 6.5.0.180


### Build Image
```
cd [repo-clone]/jenkins-sencha-cmd
docker build -t jenkins-sencha-cmd .
```

### Run Image
```
docker run --name=jenkins-sencha-cmd -p 8080:8080 -p 50000:50000 -d jenkins-sencha-cmd
```

#### Inital Admin Password
```
docker cp [containerid]:/var/jenkins_home ./dump
```
Then retrieve the password by opening the /dump/secrets/initialAdminPassord file.
