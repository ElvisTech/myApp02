pipeline {
    agent any

    stages {
        stage('PHP deploy app') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'MyLamp', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.php')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
        stage('notify') {
            steps {
                slackSend channel: '#curso-devops', message: 'test de despliegue de app desde github'
            }
        }
    }
}
