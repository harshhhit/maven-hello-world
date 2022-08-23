pipeline{
    agent any
    tools{
        maven "maven"
    }

    stages{
        stage('build') {
            steps{
                sh 'mvn clean package compile'
            }
            post{
                success{
                    echo"Archiving rhe Artifact"
                archivingArtifacts '**/target/*.war'
                }
                
            
            }

        }
    }
    stage ('Deploy to tomcat server') {
      steps{
        deploy adapters: [tomcat9(credentialsId: '0ed3351a-8b1b-4366-a7be-d46ca7ea715d', path: '', url: 'http://ec2-43-204-23-125.ap-south-1.compute.amazonaws.com:8081/')], contextPath: null, war: '**/.wae'

      }  
    }
}
     
