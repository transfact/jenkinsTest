pipeline {
    agent any
    tools {nodejs "node21"}
    environment {
        NODE_ENV='production'
    }
    stages {
        stage('Source') {
            steps {
                git 'https://github.com/transfact/jenkinsTest.git'
                echo 'Index.js file content'
                sh 'cat index.js'
            }
        }
        stage('Build') {
            environment {
                NODE_ENV='staging'
            }  
            steps {
                echo NODE_ENV
                withCredentials([string(credentialsId: '2bfc3caf-a005-438f-b742-c5101ba2b882', variable: 'sv')]) {
                    echo sv
                    // some block
                }
                sh 'npm install'
            }
        }
        stage('save Artifact') {
            steps {
                archiveArtifacts artifacts: '**', followSymlinks: false
            }
        }
    }
}
