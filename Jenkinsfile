pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    environment{
       ArtifactId = readMavenPom().getArtifactId()
       Version = readMavenPom().getVersion()
       Name = readMavenPom().getName()
       GroupId = readMavenPom().getGroupId()
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
                script {
                
                 def NexusRepo = Version.endsWith("SNAPSHOT") ? "ikeDevOpsLab-SNAPSHOT" : "ikeDevOpsLab-RELEASE"      
                nexusArtifactUploader artifacts: 
                 [[artifactId: "${ArtifactId}",  
                 classifier: '', 
                 file: "target/${ArtifactId}-${Version}.war", 
                 type: 'war']], 
                 credentialsId: 'b814b22e-d57d-40a4-bce5-739c977a3eb6', 
                 groupId: "${GroupId}", 
                 nexusUrl: '172.36.22.60:8081', 
                 nexusVersion: 'nexus3', 
                 protocol: 'http', 
                 repository: "${NexusRepo}", 
                 version: "${Version}"

                }
            }
        }

        // Stage 4 : Print some information
        stage ('Print Environment variables'){
                    steps {
                        echo "Artifact ID is '${ArtifactId}'"
                        echo "Version is '${Version}'"
                        echo "GroupID is '${GroupId}'"
                        echo "Name is '${Name}'"
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