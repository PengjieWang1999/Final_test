def RUN = true //Whether to Run the Code
def BUILD_NAME = "Latest" //Name of the build

/* Pengjie Wang A01061599 20200414 Final */

pipeline {

    agent any
    
    stages {
        stage('Build') {
            steps {
                echo "Starting Build..."
                sh 'mvn -B -DskipTests clean package'
                echo "Build Complete."
            }
        }
        stage('Code Quantity') {
            steps {
                sh "wc -l src/main/java/com/mycompany/app/App.java"
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Run') {
            when {
              expression {
                RUN == true
              }
            }
            steps {
                sh './deliver.sh'
            }
        }
        stage('Build Results') {
            steps {
                echo "Build ${BUILD_NAME} completed successfully."
                echo "I have now completed ACIT 4850!"
            }
        }
    }
}
