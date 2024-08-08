pipeline {
    agent {label 'linux_slave2'}

    stages {
        stage('Compile') {
            steps {
               echo "compiling teh code"
            }
        }
        stage('UnitTest') {
            steps {
               echo "Test teh code"
            }
        }
        stage('Package') {
            steps {
               echo "Package teh code"
            }
        }
    }
}
