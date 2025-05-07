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
        stage('print all env vars') {
    steps {
        sh 'printenv'
    }
}
        stage('checking mvn HOME_PATH') {
            steps {
                sh ''' 
                    echo $M2_HOME
                '''
            }
        }
    }
}
