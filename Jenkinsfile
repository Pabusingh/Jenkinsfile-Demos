pipeline{    
    agent any
    environment{
        IMAGE_BUILD_ARTIFACT = "image_build_details"
        DOCKER_DIR=""
    }
    stages{
        stage("A"){
            steps{
                
                sh '''#!/bin/bash
                    echo $PWD
                    dockerfile_dir=()
                    dir_list=$(find . -maxdepth 1 -mindepth 1 -type d -printf '%f ')
                    for dir in $dir_list
                    do
                        echo "Checking if readme file exists in $dir"
                        if [ -f "$dir/README.md" ]; then

                            echo "================README.md exists in $dir.===========" 
                            dockerfile_dir+=("$dir")                           
                        else
                            echo "================README.md doesn't exist in $dir.==========="
                        fi
                    done                
                    echo "Readme directorees, $dockerfile_dir"
                    for value in "${dockerfile_dir[@]}"
                    do
                        echo "value from array $value"
                    done
                    DOCKER_DIR=$dockerfile_dir    
                '''
                script{
                    def tests = [:]
                    tests = env.DOCKER_DIR
                }
                // script{
                //     def list = []
                //     // dh = new File('.')
                //     // dh.eachDir {
                //     //     def name = it.name// println(it)
                //     //     // list.add(it)
                //     //     it.eachFileMatch("README.md"){
                //     //     // println(it.dir)
                //     //         println(name)
                //     //         list.add(name)
                //     //     }
                //     // }
                //     // println(list)
                //     // echo "List $list"


            }            
        }
    }    
}