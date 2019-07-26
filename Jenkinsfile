pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'java'
    }

    stages {
        stage('Clean-workspace') {
            steps {
                cleanWs()
            }
        }
        stage('src-checkout') {
            steps {
                git branch: 'master',
                //credentialsId: '12345-1234-4696-af25-123455',
                url: 'https://github.com/parasuthulasi/perficient.git'
            }
        }
        stage('Deploy') {
            steps {
                    rtMavenRun (
                    pom: 'pom.xml', goals: 'clean install'
                )
            }
 // for downloadin files           
        rtDownload (
    serverId: "Artifactory-1",
    spec:
        """{
          "files": [
            {
              "pattern": "bazinga-repo/froggy-files/",
              "target": "bazinga/,
            }
         ]
        }"""
            
// for downloading files            
)    
        }
    }
}
