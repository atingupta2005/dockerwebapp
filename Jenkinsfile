node {

    checkout scm

    docker.withRegistry('https://atttrainings.jfrog.io', 'jfrog-dockerhub') {
        def customImage = docker.build("atttrainings.jfrog.io/docker-local/dockerwebapp:${env.BUILD_ID}")

        /* Push the container to the custom Registry */
        customImage.push()
    }
    
   stage('HelloWorld') {
    echo 'Hello World'
  }
}
