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
                script{
                    def list = []
                    dh = new File('.')
                    dh.eachDir {
                        def name = it.name// println(it)
                        // list.add(it)
                        it.eachFileMatch("README.md"){
                        // println(it.dir)
                            println(name)
                            list.add(name)
                        }
                    }
                    println(list)
                }
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