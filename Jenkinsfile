pipeline {

  environment {
    dockerimagename = "andr35/nodeejemplo.v1"
    dockerImage = ""
    KUBECONFIG_CREDENTIAL_ID = "myconfigk8s"
  }

  agent any

  stages {

    stage('Checkout Source') {
      steps {
        echo 'Chechout Source'
       //   git 'https://github.com/Bravinsimiyu/jenkins-kubernetes-deployment.git'
      }
    }

    stage('Build image') {
      steps{
        echo 'Checkout Image'
       // script {
       //   dockerImage = docker.build dockerimagename
       // }
      }
    }

    stage('Pushing Image') {
      environment {
               registryCredential = 'dockerhub-credentials'
           }
      steps{
          echo 'Pushing Image'
        //script {
         // docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
         //   dockerImage.push("latest")
          //}
        }
    }

    stage('Deploying App to Kubernetes') {
      steps {
        script {
           // kubernetesDeploy(configs: "deployment.yaml", "service.yaml")
           withKubeConfig([credentialsId: 'myconfigk8s']) {
                    sh "kubectl get pod"
                }
        }
      }
    }
   }
}

 