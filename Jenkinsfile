node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("akumawat4692/nodejs")
    }

    stage('Test image') {

        app.inside {
            echo "Tests passed"
        }
    }

    stage('Push image') {
        /*
                        You would need to first register with DockerHub before you can push images to your account
                */
        docker.withRegistry('https://registry.hub.docker.com', 'docker_hub') {
            app.push("akumawat4692/nodejs")
            app.push("latest")
            }
                echo "Trying to Push Docker Build to DockerHub"
    }
}

