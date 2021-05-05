pipeline {
  
  agent any
  
  stages {
    
    stage("Build"){
      
      steps {
        echo 'Modify building the application...'
        git log --oneline -1 ${GIT_COMMIT}
      }
    }
      
    stage ("test"){
      
      steps{
        echo 'testing the application...'
      }
    }
      
    stage ("deploy"){
      steps{
        echo 'deploying the application'
      }
    }
  }
  

}
