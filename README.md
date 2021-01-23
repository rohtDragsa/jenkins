# Local setup

- Jenkins on the VM
- user ngrok
- setup github withy ngrok address

- install github integration plugin in jenkins
- add webhook to the repo `http://xxxx.ngrok.io/github-webhook/`
- ?

# jenkins

https://www.youtube.com/watch?v=6BIry0cepz4

**environment**

```groovy
pipeline {
    agent any
    environment { //This env will be available in all pipeline
        HELLO = 'world'
    }

    stages {
        ...
    }
}
```

**paramiters**
