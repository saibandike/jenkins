pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                sh './build.sh' // or 'mvn clean install' for Maven projects
            }
        }

        stage('Test') {
            steps {
                sh './run-tests.sh'
            }
        }

        stage('Deploy') {
            steps {
                sshPublisher(
                    publishers: [
                        sshPublisherDesc(
                            configName: 'server',
                            transfers: [
                                sshTransfer(
                                    sourceFiles: '**/*.jar',
                                    remoteDirectory: '/deploy/path'
                                )
                            ]
                        )
                    ]
                )
            }
        }
    }
}
