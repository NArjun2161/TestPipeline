pipeline {
    agent any

    stages {
        stage('checking versions of tools') {
            steps {
                sh ''' 
                    git --version
                    mvn -v
                    java --version
                '''
            }
        }
    }
}
