node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
                            steps {
                                dir(pwd()) {
                                    app = docker.build("princy/hellonode")
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
