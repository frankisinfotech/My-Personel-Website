pipeline {
    agent any
    stages {
        stage ('Get EnvVar') {
            steps {
                sh 'printenv'
            }
        }
        stage ('Build') {
            steps {
                sh 'docker build -t frankisinfotech/webapp:""$BUILD_ID"" .'
            }
        }
        stage ('Push to Docker') {
            steps {
                withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
                   sh 'docker push frankisinfotech/webapp:""$GIT_COMMIT""'
            }
           }
        }
    }
}
