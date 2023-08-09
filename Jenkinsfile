pipeline {
    agent any
    environment {
        GITHUB_REPO_URL = 'https://github.com/ashahidkhattak/test.git'
        LINUX_SERVER = '192.168.1.13'
        LINUX_USERNAME = 'osboxes'
        LINUX_DESTINATION = './testweb/'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Clone the GitHub repository
                    bat "git clone ${env.GITHUB_REPO_URL}"
                }
            }
        }

        stage('Deploy to Linux') {
            steps {
                script {
                    // Copy the extracted files to the Linux server
                        bat '''
                        pscp -pw osboxex.org "C:\\Users\\AbdulShahid\\testweb" osboxex@${env.LINUX_SERVER}:${env.LINUX_DESTINATION}
                        '''
                }
            }
        }
    }

    post {
        always {
            // Clean up workspace
            deleteDir()
        }
    }
}
