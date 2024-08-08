pipeline {
    agent { label 'linux_slave2' }
    tools {
        maven 'mymaven' // This should match the name in Global Tool Configuration
        jdk 'myjdk'     // This should match the name in Global Tool Configuration
        
    }
    parameters {
        string(name: 'ENV', defaultValue: 'DEV', description: 'COMPILER ENV?')
        booleanParam(name: 'EXECUTETEST', defaultValue: true, description: 'EXECUTE this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        choice(name: 'APPVERSION', choices: ['1.1', '1.2', '1.3'], description: 'Pick something')
    }
    stages {
        stage('Compile') {
            steps {
                script {
                    echo "Compiling in ${params.ENV}"
                }
                sh 'mvn compile'
            }
        }
        stage('UnitTest') {
            when {
                expression { params.EXECUTETEST == true }
            }
            steps {
                script {
                    echo "Testing the code"
                    sh 'mvn test'
                }
            }
        }
        stage('Package') {
            steps {
                script {
                    echo "Packaging the code"
                    sh 'mvn package'
                }
            }
        }
        stage('Example') {
            input {
                message "Should we continue?"
                ok "Yes, should be."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                script {
                    echo "Hello, ${params.PERSON}, nice to meet you."
                }
            }
        }
    }
}
