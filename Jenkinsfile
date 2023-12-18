pipeline {
    agent any
    options {
        timeout(time: 30, unit: 'MINUTES')
    }
    triggers {
        pollSCM('* * * * *')
    }
    tools {
        maven 'MVN_HOME'
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/spring-projects/spring-framework.git',
                    branch: 'main'
            }
        }
        stage('SonarQube_analysis') {
            steps {

                // performing sonarqube analysis with "withSonarQubeENV(<Name of Server configured in Jenkins>)"
                withSonarQubeEnv('SONAR_CLOUD') {
                // requires SonarQube Scanner for Maven 3.2+
                sh 'mvn clean package sonar:sonar -Dsonar.organization=Prabhu402'
                }
            }
        }


        stage('reporting_junit') {
            steps {
                junit testResults: '**/target/surefire-reports/TEST-*.xml'
            }
        }
    }

}
