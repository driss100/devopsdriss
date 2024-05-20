pipeline {
    agent any
    tools{
        maven 'maven_3_5_0'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/driss100/devopsdriss']])
                bat 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    bat 'docker build -t drdiaz/devops-integration .'
                }
            }
        }
        stage('push hub image'){
            steps{
                script{

                    bat 'docker login -u drdiaz -p Amina100@'
                    bat 'docker push drdiaz/devops-integration'
                }
            }
        }
    }
}