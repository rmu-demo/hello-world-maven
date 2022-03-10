pipeline {
    agent any
    tools {
        maven 'Maven 3.8.4'
        jdk 'jdk9'
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
                stash 'build-artifact'
            }
        }

        stage('Test') {
            parallel {
                stage('Part 1') {
                    agent any
                    tools {
                        maven 'Maven 3.8.4'
                        jdk 'jdk9'
                    }
                    steps {
                        unstash 'build-artifact'
                        sh 'mvn test'
                    }
                }
                stage('Part 2') {
                    agent any
                    tools {
                        maven 'Maven 3.8.4'
                        jdk 'jdk9'
                    }
                    steps {
                        unstash 'build-artifact'
                        sh 'mvn test'
                    }
                }
                stage('Part 3') {
                    agent any
                    tools {
                        maven 'Maven 3.8.4'
                        jdk 'jdk9'
                    }
                    steps {
                        unstash 'build-artifact'
                        sh 'mvn test'
                    }
                }
            }
        }
    }
}