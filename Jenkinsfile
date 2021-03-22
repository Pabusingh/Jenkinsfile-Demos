pipeline{    
    agent any
    environment{
        IMAGE_BUILD_ARTIFACT = "image_build_details"
    }
    stages{
        stage("A"){
            steps{
                 sh '''#!/bin/bash
                    echo $PWD              
                '''
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}