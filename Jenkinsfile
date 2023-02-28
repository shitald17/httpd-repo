pipeline{
  agent{
    label{
        label "built-in"
    }

  }
  stages{
    stage("clean Workspace"){
      steps{
             cleanWs()
           }
          }
    stage("checkout_code_from_SCM"){
      steps{
             checkout scm
           }
          }
     stage("creating_docker_container_on_jenkins_master"){
       steps{
            sh '''
                sudo docker rm --force httpd-1
                sudo docker run -itdp 80:80 --name httpd-1 httpd
            '''
             }
            }
     stage("copying_index_file_in_repo_contaners"){
        steps{
                sh '''
                    sudo docker cp $WORKSPACE/index.html httpd-1:/usr/local/apache2/htdocs/ 
                '''
             }
            } 
            
    }
} 
