# DOCKER FILES

## jenkins-sencha-cmd

Includes:

    - jenkins
    - jenkins plugins
        + git plugin
    - Sencha Cmd 6.1.3.42


### Build Image

```
cd [repo-clone]/jenkins-sencha-cmd
docker build -t elmasse/jenkins-sencha-cmd .
```

### Run Image

```
docker run --name=jenkins-sencha-cmd -p 8080:8080 -p 50000:50000 -d elmasse/jenkins-sencha-cmd
```

