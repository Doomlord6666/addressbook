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

        stage ('Parallel block'){
            Parallel{
                stage ('Code Compile 1'){
                    steps{
                        catchError (buildResult: 'SUCCESS',stageResult: 'FAILURE'){
                        sh """
                        echo compile the 
                        mvn compile
                        """
                        }
                    }
                } 
                stage ('Code Validate 1'){
                    steps{
                        catchError (buildResult: 'SUCCESS',stageResult: 'FAILURE'){
                        sh """
                        mvn validate
                        """
                        }
                    }
                }        
            }
        }    
     
        stage ('Test errorcatch'){
            steps{
                sh"""
                echo demo
                """
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

        stage ('Package the code'){
            steps{
                sh"""
                mvn package
                """
            }

        }
    }
  }
