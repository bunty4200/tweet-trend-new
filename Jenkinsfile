pipeline{
    agent{
        node{
            label 'maven'
        }
    }

environment {
    PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
}
    stages{
        stage('build'){
            steps{
                echo "-----------------Deploy build started--------------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo "-----------------Depoly build stopped----------------"
            }
        }

        stage('test'){
            steps{
                echo "------------------Test build started---------------"
                sh 'mvn surefire-report:report'
                echo "------------------Test build stopped----------------"
            }
        }

    stage('SonarQube analysis') {
    environment{
        scannerHome = tool 'valaxy-sonar-scanner'
    }
    steps{
    withSonarQubeEnv('valaxy-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
            }
       }
     }

    }
}