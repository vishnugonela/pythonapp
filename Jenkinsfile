pipeline{
  agent any

  stages{
    stage('Image_build'){
      steps {
      sh '''
        echo "Docker image building "
        rm -rf ${WORKSPACE}/myapp && mkdir -p ${WORKSPACE}/myapp
        cd ${WORKSPACE}/myapp && git clone --branch main https://github.com/vishnugonela/pythonapp.git
        
        docker image build -t pythonapp:latest ${WORKSPACE}/myapp/pythonapp
      '''
      }
    }

    stage('image_tagging'){
      steps {
        sh '''
          echo "Image taggging ..."
          docker image tag pythonapp:latest vishnugonela/pythonapp:3.0

          '''
      }
    }

    stage('docker_hub_push'){
      steps {
        sh '''
          echo "Image pushing to repo"
          docker image push vishnugonela/pythonapp:3.0
          
        '''
      }
    }

    stage('app_deployment'){
      steps {
        sh '''
          echo "Docker App deployment"
          docker container rm -f container1 2> /dev/null
          docker container run -d --name container1 -p 8081:8000 vishnugonela/pythonapp:3.0

          echo "Validating Container app"
          sleep 30
          docker container ls | grep container1

        '''
      }
    }
  }
  
}
