def skip = false

pipeline {
  
  agent any
  
  environment {
    COMMITMESSAGE = sh(script: 'git log --format=format:%s -1', , returnStdout: true).trim()
  }
  
  stages {
    
    stage("Build"){
      
      steps {
        echo "COMMITMESSAGE = ${env.COMMITMESSAGE}"
        
        script {
            skip = true
        }
        
        echo 'Modify building the application...'
        echo ' SHA and title'
        sh 'git log --oneline -1 ${GIT_COMMIT}'
        echo 'latest commit'
        sh 'git log --format=format:%s -1'
        echo 'print commit, author, date, title & commit message'
        sh 'git log --format="medium" -1 ${GIT_COMMIT}'
        
        echo "COMMITMESSAGE = ${env.COMMITMESSAGE}"
      }
    }
      
    stage ("test"){
      when{
          expression{
              !skip
          }
      }
      
      steps{
        echo 'testing the application...'
      }
    }
      
    stage ("deploy"){
        when{
          expression{
              !skip
          }
      }
      
      steps{
        echo 'deploying the application'
      }
    }
  }
  

}
