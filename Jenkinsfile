pipeline{
    agent { label 'maven' }
    options {
        timeout (time: 30, unit: 'MINUTES' )
    }https://github.com/Prabhu028/spring-petclinic1/blob/main/Jenkinsfile
    triggers {
        pollSCM ('* * * * *')
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
