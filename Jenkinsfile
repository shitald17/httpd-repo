pipeline{
  agent{
    label{
        label "built-in"
        customWorkspace "/mnt/jenkins-master/"
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
                sudo docker rm --force httpd-3
                sudo docker run -itdp 82:80 --name httpd-3 httpd
            '''
             }
            }
     stage("copying_index_file_in_repo_contaners"){
        steps{
                sh '''
                    sudo chmod 777 /mnt/jenkins-master/index.html
                    sudo docker cp /mnt/jenkins-master/index.html httpd-3:/usr/local/apache2/htdocs/
                '''
             }
            } 
            
    }
} 
