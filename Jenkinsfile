#!/usr/bin/env groovy

node{
    stage('Git') {
        git 'https://github.com/Sri1983/DevOpsClassCodes.git'
    }
    
    stage ('Compile') {
        withMaven (maven:'MyMaven'){
        sh 'mvn compile'
    }
    }
    stage ('Test') {
        try{ 
            withMaven(maven:'MyMaven'){
                sh 'mvn test'
            }
            
           } finally{
               junit 'target/surefire-reports/*.xml'
        }
    }
    stage ('Package'){
        withMaven(maven:'MyMaven'){
            sh 'mvn package'
        }
        
    }
}
