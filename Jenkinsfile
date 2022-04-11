node{
    stage('SCM Checkout'){
      git branch: 'main', credentialsId: 'pipeline', url: 'https://github.com/Odunade/docker-web-app.git'
    }
    stage('Mvn Package'){
      def mvnHome = tool name: 'maven-3', type: 'maven'
    
    }
    stage('Build Docker Image'){
      sh 'docker build -t odunade/my-images:1.0.0 .'
    }
    stage('push Docker Image'){
      withCredentials([string(credentialsId: 'dock-Pwd', variable: 'dockerHubPwd')]) {
        sh "docker login -u odunade -p ${dockerHubPwd}"

      }
      sh 'docker push odunade/my-images:1.2'
    }
    stage('Run Container on Dev Server'){
      def dockerRun = 'docker run -p 8080:8080 -d --name my-images odunade/my-images:1.0.0'
        sshagent(['dev-server']){
          sh "ssh -o StrictHostKeyChecking=no ubuntu@172.31.6.252 ${dockerRun}"
        
        }  
    
    }   

} 
