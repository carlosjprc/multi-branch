pipeline {
  agent {
    node {
      label 'principal'
    }
  }
  
  options {
    // Para ficheros de log 
    buildDiscarder logRotator(
      daysToKeepStr: '15',
      numToKeepStr: '10'
    )
  }
  
  stages {
    stage('Cleanup Workspace') {
      steps {
       cleanWs()
       echo "Eliminado WorkSpace para Proyecto"
      }
    }
    
    stage('Code Checkout') {
      steps {
       checkout(
        $class: 'GitSCM',
        branches: [[name: '+/master']],
        userRemoteConfigs: [[url: 'https://github.com/josmarjim86/spring-petclinic.git']]
       )
      }
    }
    
    stage('Unit Testing') {
      steps {
       echo "Running Unit Test"
      }
    }
    
    stage('Code Analysis') {
      steps {
       echo "Running Code Analysis"
      }
    }
    
    stage('Build Deploy Code') {
      
      when {
       branch 'developer' 
      }
      
      steps {
       echo "Building Artifact"
       echo "Deploying Code"
      }
    }
    
  }
    
}
