def skip = true

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
            if ((env.COMMITMESSAGE).contains("ci deploy")){
                skip = false
            }

        }
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
