pipeline {
    agent any

    environment {
        M2_HOME = '/usr/share/maven' // Optional, if needed for reference
    }

    stages {
        stage('Checking Versions of Tools') {
            steps {
                sh ''' 
                    git --version
                    mvn -v
                    java --version
                '''
            }
        }

        stage('Print All Env Vars') {
            steps {
                sh 'printenv'
            }
        }

        stage('Checkout') {
            steps {
                git url: 'https://github.com/NArjun2161/makemytrip26.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Clean and Package') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Publish Test Results') {
            steps {
                junit '**/target/surefire-reports/*.xml'
            }
        }

        stage('Archive Build Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }

        stage('Complete Pipeline') {
            steps {
                echo '✅ Arjun Pipeline executed successfully!'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
