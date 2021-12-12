pipeline {
    agent any 
    stages {
        


        stage('Build Docker image'){
            steps {
                sh 'docker build -t 9526584898/docker_jenkins_pipeline:${BUILD_NUMBER} .'
            }
        }

        stage('Docker Login'){
            
            steps {
                withCredentials([string(credentialsId: 'dockerpwd', variable: 'dockerpwd')]){
                    sh "docker login -u 9526584898 -p ${dockerpwd}"
                }
            }                
        }

        stage('Docker Push'){
            steps {
                sh 'docker push 9526584898/docker_jenkins_pipeline:${BUILD_NUMBER}'
            }
        }
        
       

        
        stage('Archving') { 
            steps {
                 archiveArtifacts '**/target/*.jar'
            }
        }
    }
}
