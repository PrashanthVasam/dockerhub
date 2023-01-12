node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("prashanthvasam/dockerhub")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }
    environment {     
    DOCKERHUB_CREDENTIALS= credentials('1234567890')     
} 
        stage('Login to Docker Hub') {      	
    steps{                       	
	sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'                		
	echo 'Login Completed'      
    }           
}   
    stage('Push Image to Docker Hub') {         
    steps{                            
 sh 'sudo docker push prashanthvasam9676/docker-test:$BUILD_NUMBER'           
echo 'Push Image Completed'       
    }            
}  
    
}
