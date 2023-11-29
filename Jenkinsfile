pipeline{
    agent any
    options {
        timeout (time: 1, unit: 'HOURS' )
    }
    triggers {
        pollscm ('* * * * *')
    }
    stages {
        stage('gitsc') {
            steps {
                git url: 'https://github.com/Prabhu028/spring-petclinic1.git', 
                    branch: 'main'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
                archiveArtifacts artifacts: '**/spring-petclinic-*.jar'
                junit testResults: '**/TEST-*.xml'
                
            }
        }

    }
}