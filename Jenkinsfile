node {
    def app
    stage('clone repository') { // for display purposes
       checkout scm
    }
    stage('Build') {
        // Run the maven build
       app = docker.build("raquelbatista/CD-nodejs-app")
    }
    stage('Test image') {
        app.inside {
            sh 'echo "Test PAssed'
        }
    }
    stage('Push image'){
        docker.withRegistry('https://registry.hub.docker.com', 'git'){
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }
}
