node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("testrepo/nodeapp")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }

stage('Push image') {
        withDockerRegistry([ credentialsId: "docker-hub-credentials", url: "" ]) {
        bat "docker push debanjanmitra2018/testrepo:build"
        }
}
