pipeline{
    agent{
        node{
            label 'maven'
        }
    }
    
    stages{
        stage('Clone-code'){
            steps{
                git branch: 'main', url: 'https://github.com/bunty4200/tweet-trend-new.git'
            }
        }
    }
}