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
                sudo docker run -itdp 81:80 --name httpd-2 httpd
            '''
             }
            }
     stage("copying_index_file_in_repo_contaners"){
        steps{
                sh '''
                    sudo docker cp $WORKSPACE/index.html httpd-2:/usr/local/apache2/htdocs/
                '''
             }
            } 
            
    }
} 
