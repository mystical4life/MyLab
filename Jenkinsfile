pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    
   
    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }

        // Stage3 : publis the artifact to Nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'ikeDevOpsLab', classifier: '', file: 'target/ikeDevOpsLab-0.0.14-SNAPSHOT.war', type: 'war']], credentialsId: '3594602f-d4f2-4df6-aeea-bee3afe852e7', groupId: 'com.ikedevopslab', nexusUrl: '172.20.10.30:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'IkeDevopsLab-SNAPSHOT', version: '0.0.14-SNAPSHOT'

            }
        }

        // Stage5 : deploying
        stage ('Deploy'){
            steps {
                echo ' testing......'
                
                
            
            }
        }




    }

}