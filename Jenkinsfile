node {

    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {

        def customImage = docker.build("atingupta2005/dockerwebapp:${env.BUILD_ID}")

        /* Push the container to the custom Registry */
        customImage.push()
    }
   
    stage ('Push image to Artifactory') {
        steps {
            rtDockerPush(
                serverId: "jfrogid1",
                image: "atingupta2005/dockerwebapp:${env.BUILD_ID}",
                //host: HOST_NAME,
                targetRepo: 'docker-local', // where to copy to (from docker-virtual)
                // Attach custom properties to the published artifacts:
                properties: 'project-name=docker1;status=stable'
            )
        }
    }
    
}
