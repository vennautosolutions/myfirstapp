node {
  def image
   
   stage ('Build') {
         sh "mvn clean package"           
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
