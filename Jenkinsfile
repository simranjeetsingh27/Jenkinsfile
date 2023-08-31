    pipeline {

    agent any

    stages {

        stage("Delete") {
            parallel {
                stage("ssh") {
                    when { expression { params.Delete == "ssh" } }
                    steps {
                        sh '''
                #!/bin/bash
                curl -X DELETE 'http://admin:113ea56fc33a1@18.204.211.163:8080//credentials/store/system/domain/_/credential/ab347119-9e7a-4336-904d-42a6f7713750/delete' --data-urlencode 'json={
                  "": "0",
                  "credentials": {
                    "scope": "GLOBAL",
                    "id": "'"$id"'",
                    "username": "'"$username"'",
                    "Private Key": "'"$key"'",
                    "description": "",
                    "$class": "com.cloudbees.jenkins.plugins.sshcredentials.impl.BasicSSHUserPrivateKey"
                  }
                    }'
                    '''
                    }
                }
                stage("username") {
                    environment { 
                        username = "$username"
                        password = "$password"
                    }

                    when { expression { params.Delete == "username" } }
                    steps {
                        echo "username is $username"
                        sh '''
                #!/bin/bash
                curl -X DELETE 'http://admin:113e9a4b1@18.204.211.163:8080/credentials/store/system/domain/_/createCredentials' --data-urlencode 'json={
                  "": "0",
                  "credentials": {
                    "scope": "GLOBAL",
                    "id": "'"$id"'",
                    "username": "'"$username"'",
                    "password": "'"$password"'",
                    "description": "",
                    "$class": "com.cloudbees.plugins.credentials.impl.UsernamePasswordCredentialsImpl"
                  }
                    }'
                    '''
                    }
                }
                stage("secret") {
                    when { expression { params.Delete == "secret" } }
                    steps {
                        sh '''
                #!/bin/bash
                curl -X DELETE 'http://admin:113ea56b542086fc33aa33ebdc3849a4b1@18.204.211.163:8080/credentials/store/system/domain/_/createCredentials' --data-urlencode 'json={
                  "": "0",
                  "credentials": {
                    "scope": "GLOBAL",
                    "id": "'"$id"'",
                    "secret": "'"$secret"'",
                    "description": "",
                    "$class": "org.jenkinsci.plugins.plaincredentials.impl.StringCredentialsImpl"
                  }
                    }'
                    '''
                    }
                }
            }
       }   
       
    }
}



