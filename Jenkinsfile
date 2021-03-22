pipeline{    
    agent any
    stages{
        stage("A"){
            steps{
                 sh '''#!/bin/bash
              echo $PWD

              git_hash=`echo $GIT_COMMIT | cut -c -8`
              if [[ "$GIT_BRANCH" == "origin/"* ]]; then
                  image_tag=`echo $GIT_BRANCH | cut -c 8-`
                  image_tag="$image_tag-$git_hash"
              elif [ "$GIT_BRANCH" = "detached" ]; then
                  image_tag="$git_hash"
              else
                  image_tag="$GIT_BRANCH-$git_hash"
              fi
              echo "============================================"
              echo ""
              echo "Git branch: $GIT_BRANCH"
              echo "Git commit: $GIT_COMMIT"              
              echo "Calculated docker image tag: $image_tag"
              
              echo "DOCKER_IMAGE_TAG=$image_tag" > $IMAGE_BUILD_ARTIFACT
              echo $image_tag > "output.txt"
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