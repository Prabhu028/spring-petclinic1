pipeline{
    #agent 
    options {
        timeout (time: 30, unit: 'MINUTES' )
    }
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
                sh 'mvn clean package'
                archiveArtifacts artifacts: '**/spring-petclinic-*.jar'
                junit testResults: '**/TEST-*.xml'
                
            }
        }

    }
}
