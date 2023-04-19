node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stages {
        stage('Build image') {
            steps {
                dir(pwd()) {
                    sh 'docker build -t princy/hellonode .'
                }
            }
        }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            app=docker.run("princy/hellonode")
//             bat 'echo "Tests passed"'
        }
    }

//     stage('Push image') {
//         /* Finally, we'll push the image with two tags:
//          * First, the incremental build number from Jenkins
//          * Second, the 'latest' tag.
//          * Pushing multiple tags is cheap, as all the layers are reused. 
//          *docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials'*/
//            sh 'sudo docker login -u "upasanatestdocker" -p "Zephyr@17" docker.io'
               
//             app.push("${env.BUILD_NUMBER}")
//             app.push("latest")
        
//     }
}
