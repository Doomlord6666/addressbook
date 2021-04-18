pipeline {
      agent {
          label 'master'
      }
      
      tools {
          maven 'mymaven'
          jdk 'myjava' 
      }
      
    stages {
        stage ('Code Compile'){
            steps{
                catchError (buildResult: 'SUCCESS',stageResult: 'FAILURE'){
                sh """
                echo compile the 
                mvn compile
                """
                }
            }

        }
        
        stage ('JUNIT Test'){
            steps{
                sh """
                echo compile the code
                mvn test
                """
            }

        }   
       
          stage ('Test errorcatch'){
            steps{
                sh"""
                echo demo
                """
            }

        }     
        stage ('Package the code'){
            steps{
                sh"""
                mvn package
                """
            }

        }
        
    }
  }
