pipeline{
    agent any
    tools {
  maven 'maven3'
}

    stages{
        stage('Git checkout'){
            steps{
               git credentialsId: 'git', url: 'https://github.com/Eluri1423/springmvc'
            }
        }
        stage('Maven Build'){
            steps{
            sh 'mvn clean package'
            }
        }   
        stage('Tomcat Deploy'){
            steps{
                sshPublisher(publishers: [sshPublisherDesc(configName: 'tomcat9', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '''/opt/tomcat9/bin/shutdown.sh
/opt/tomcat9/bin/startup.sh''', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: 'target/', sourceFiles: 'target/springmvc.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
    }
}
