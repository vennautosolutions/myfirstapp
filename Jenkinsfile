node {
  def image
   
   stage ('Build') {
         def mvnHome = tool name: 'Maven', type: 'maven'
         def mvnCMD = "${mvnHome}/bin/mvn "
         sh "${mvnCMD} clean package"           
        }
    stage('Build image') {
  
       app = docker.build("charlesaparasa/springboot")
    }

    stage('Push image to gcr') {
        docker.withRegistry('https://registry.hub.docker.com', 'charlesparasa:Para@12char') {
            app.push("${env.BUILD_NUMBER}")
        }
    }    
}
