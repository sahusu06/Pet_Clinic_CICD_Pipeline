pipeline 
{
    agent { label 'Image_Server' }
    
     environment {
        SONAR_PROJECT_KEY = 'Pet'
        SONAR_PROJECT_NAME = 'Pet'
        SONAR_HOST_URL = 'http://20.244.3.245:9000'
        SONAR_TOKEN = 'sqp_1e210b5f33c5089938e46e4b6714bb4e1a52bc6c'
    }
    
    stages 
    {
        stage('Delete Repository') 
        {
            steps 
            {
                // Delete the Git repository using Git commands
                deleteDir() // Replace with the actual path to your repository
            }
        }
        stage ('Pull Project from Git Hub') 
        {
            steps 
            {
                // Get some code from a GitHub repository
                checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://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@github.com/sahusu06/spring-petclinic.git']]])
                //git 'https://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@github.com/sahusu06/spring-petclinic.git'

            }
        }
        stage('Build the code')
        { 
            steps
            {
                withMaven(maven: 'MAVEN')
                {
                    sh 'mvn deploy'
                }
            }
        }
        
        
        stage('Build and Analyze') {
            steps {
                script {
                    // Run Maven build with SonarQube analysis
                    withMaven(maven: 'MAVEN') {
                        sh "mvn sonar:sonar " +
                           "-Dsonar.projectKey=${SONAR_PROJECT_KEY} " +
                           "-Dsonar.projectName=${SONAR_PROJECT_NAME} " +
                           "-Dsonar.host.url=${SONAR_HOST_URL} " +
                           "-Dsonar.login=${SONAR_TOKEN}"
                    }
                }
            }
        }
    
       
         stage('Ansible: Copy Jar file')
        {
            steps
            {
                ansiblePlaybook  credentialsId: 'root', installation: 'Ansible', inventory: '/etc/ansible/hosts', playbook: '/etc/ansible/copy_artefact.yml'
            }
        }
         stage('Ansible: Create Image and run container')
        {
            steps
            {
                ansiblePlaybook  credentialsId: 'root', installation: 'Ansible', inventory: '/etc/ansible/hosts', playbook: '/etc/ansible/create_image.yml'
            }
        }
    }
}
