pipeline{
    agent any

    stages{
        stage('checkout'){
            steps{
              git branch: 'main', credentialsId: 'Git-cred', url: 'https://github.com/gopinathbca35/MavenHelloWorld.git'
            }
        }
        stage('build'){
            steps{
               bat 'mvn compile'
            }
        }
        stage('artifact'){
            steps{
               bat 'mvn package -DskipTests'
            }
        }
        stage('artifact upload'){
            steps{
               nexusArtifactUploader artifacts: [[artifactId: 'MavenHelloWorld', classifier: '', file: 'target/MavenHelloWorld-0.2.0.jar', type: '.jar']], credentialsId: 'Nexus-cred', groupId: 'org.springframework', nexusUrl: 'localhost:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'MavenSample', version: '0.2.0'
            }
        }        
    }
}