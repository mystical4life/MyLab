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

        // Stage3 : publis the artifact to Nexus
        stage ('Publish to Nexus'){
            steps {
                script {


                def NexusRepo = Version.endsWith("SNAPSHOT") ? "IkeDevopsLab-SNAPSHOT" : "IkeDevopsLab-RELEASE"

                nexusArtifactUploader artifacts: 
                [[artifactId: "${ArtifactId}", 
                classifier: '', 
                file: "target/${ArtifactId}-${Version}.war", 
                type: 'war']], 
                credentialsId: '3594602f-d4f2-4df6-aeea-bee3afe852e7', 
                groupId: "${GroupId}", 
                nexusUrl: '172.20.10.30:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: "${NexusRepo}", 
                version: "${Version}"
            }

            }
        }

        // Stage4 : Print some information
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
    

