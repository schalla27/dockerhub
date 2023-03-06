node {
     def app
     stage('Clone repository') {
	checkout scm
     }
     stage('Build image') {
     app = docker.build("schalla27/abc1")
     }
     stage('Test Image') {
     app.inside{
     sh 'echo "Tests passes"' 
     }
     }
     stage('Push image') {
     docker.withRegistry('https://registry.hub.docker.com', 'git') {
     app.push("${env.BUILD_NUMBER}")
     app.push("latest")
     }
     }
}
 
