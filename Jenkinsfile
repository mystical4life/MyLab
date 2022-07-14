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

        // Stage3 : Publish the artifacts to nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.10-SNAPSHOT.war', type: 'war']], credentialsId: 'b814b22e-d57d-40a4-bce5-739c977a3eb6', groupId: 'com.vinaysdevopslab', nexusUrl: '172.36.22.60:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'ikedevopslab-SNAPSHOT', version: '0.0.10-SNAPSHOT'
            }
        }

        // Stage4 : deploying
        stage ('Deploy'){
            steps {
                echo ' testing......'

                
            
            }
        }




    }

}