pipeline {

    agent any

    stages {

        stage('Create Credntials') {

            steps {

               

                sh '''

                #!/bin/bash

                curl -X POST 'http://admin:113ea56b542086fc33aa33ebdc3849a4b1@18.204.211.163:8080/credentials/store/system/domain/_/createCredentials' --data-urlencode 'json={

                  "": "0",

                  "credentials": {

                    "scope": "GLOBAL",

                    "id": "hh",

                    "username": "'"admin"'",

                    "password": "'"admin"'",

                    "description": "",

                    "$class": "com.cloudbees.plugins.credentials.impl.UsernamePasswordCredentialsImpl"

                  }

                    }'

                    '''



            }

        }

    }

}
