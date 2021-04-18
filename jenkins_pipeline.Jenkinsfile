pipeline {
    agent {
          label 'master'
    }
      
    tools {
          maven 'mymaven'
          jdk 'myjava' 
    }
      
    stages {

        stage ('Code Compile 1'){
            steps{
                sh """
                echo compile the 
                mvn compile
                """
            }
        }

        stage ('Parallel block'){
            steps{
                Parallel{
                    stage ('Code Validate 1'){
                        steps{
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
