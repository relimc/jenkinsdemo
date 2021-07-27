pipeline {
    
    agent {
        docker {
            image 'ubuntu'
            label 'remote_jenkins'
        }
    }
    
    environment {
        TIMEZONE = 'eastern'
        TIMEZONE_DS = "${TIMEZONE}_daylight_savings"
        remote_jenkins = credentials('a3caff1a-a86b-45ca-b371-2306936e8257')
    }
    
    options {
        timestamps()
    }
    
    triggers {
        cron('*/5 * * * *')
    }
    
    stages {
        stage('dev') {
            steps {
                echo 'dev'
                sh([script: 'uname -a'])
            }
        }
        stage('test') {
            steps {
                echo 'test'
                sh 'uname -a'
                echo "${TIMEZONE}"
                echo "${TIMEZONE_DS}"
                echo "remote_jenkins: ${remote_jenkins}"
            }
        }
        stage('deploy') {
            steps {
                echo 'deploy'
            }
        }
    }
    
    post {
        always {
            echo 'post-always'
        }
    }
}
