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
                        def sourcePath = "C:\Users\AbdulShahid\testweb"
                        def remoteUsername = "osboxes"
                        def remoteHostname = "192.168.1.13"
                        def remotePath = "./testweb/"

                    // Use 'bat' step to run pscp command for copying files
                    bat """
                    "C:\\Program Files\\PuTTY\\pscp.exe" -pw osboxes.org "${sourcePath}\\*" ${remoteUsername}@${remoteHostname}:${remotePath}
                    """
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
