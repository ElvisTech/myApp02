pipeline {
    agent any

    stages {
        stage('PHP deploy app') {
            steps {
                sshPublisher(publishers: [sshPublisherDesc(configName: 'MyLamp', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/*.php')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }
        }
        stage('Sonar checking') {
            steps {
               sh '''sonar-scanner \\
                 -Dsonar.projectKey=myApp02 \\
                 -Dsonar.sources=. \\
                 -Dsonar.host.url=http://192.168.0.8:9000 \\
                 -Dsonar.login=sqp_864e4897339f6cbba874237c22b87b0ed67b75cd'''
            }
        }
        stage('notify') {
            steps {
                 slackSend channel: '#curso-devops', message: 'test de despliegue de app desde github'
            }
        }
    }
}
