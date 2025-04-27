pipeline {
    agent any  // Run the pipeline on any available agent

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Seajal-S/G-Mart.git'
            }
        }
        stage('Build') {
            steps {
                echo "Building..."
                //  No build step needed for simple HTML
            }
        }
        stage('Test') {
            steps {
                echo "Testing..."
                //  No test step.
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying..."
                // Use the ssh-steps plugin to copy files to your server
                sshPublisher(publishers: [
                    sshPublisherDesc(
                        configName: 'ecart_server',  //  Descriptive name for the server
                        transfers: [
                            fileSet(
                                dir: '.',             //  Directory containing files to transfer
                                excludes: '',
                                includes: '**/*'
                            )
                        ],
                        connection: [
                            hostName: 'ecart.com',  //  The hostname or IP address of your server
                            userName: 'Seajal',  //  The username to log in with
                            credentialId: 'server-credentials',  //  The ID of the SSH credentials you configured
                            remoteDirectory: '/var/www/ecart.com',  //  The directory on the server to deploy to
                        ],
                        failOnError: true,
                        publishEvenIfNothingToTransfer: false
                    )
                ])
            }
        }
    }
}
