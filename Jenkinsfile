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
    
    stage ('Review'){
        try{
        withMaven (maven:'MyMaven'){
        sh 'mvn pmd:pmd'
    }
        } finally{
            pmd canComputeNew: false, defaultEncoding: '', healthy: '', pattern: 'target/pmd.xml', unHealthy: ''        
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
