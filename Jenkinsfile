pipeline {
  
  agent any
  
  environment {
    COMMITMESSAGE = "test_message"
  }
  
  stages {
    
    stage("Build"){
      
      steps {
        echo 'Modify building the application...'
        echo ' SHA and title'
        sh 'git log --oneline -1 ${GIT_COMMIT}'
        echo 'latest commit'
        sh 'git log --format=format:%s -1'
        echo 'print commit, author, date, title & commit message'
        sh 'git log --format="medium" -1 ${GIT_COMMIT}'
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
