node {
  def image
   //stage ('checkout') {
   //     checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '', url: 'https://github.com/harshalkathar/myfirstapp.git']]])      
   //     }
   
   stage ('Build') {
         def mvnHome = tool name: 'maven', type: 'maven'
         def mvnCMD = "${mvnHome}/bin/mvn "
         sh "${mvnCMD} clean package"           
        }
    stage('Build image') {
  
       app = docker.build("charlesparasa/springboot")
    }

    stage('Push image to docker') {
        docker.withRegistry('https://registry.hub.docker.com', 'charlesparasa:Para@12char') {
            app.push("${env.BUILD_NUMBER}")
        }
    }       
}
