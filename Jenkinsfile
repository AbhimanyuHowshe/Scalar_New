pipeline {
    agent {label 'linux_slave2'}
    parameters {
                string(name: 'ENV', defaultValue: 'DEV', description: 'COMPILER ENV?')
                        booleanParam(name: 'EXECUTETEST', defaultValue: true, description: 'EXECUTE this value')
                                choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        choice(name: 'APPVERSION', choices: ['1.1', '1.2', '1.3'], description: 'Pick something')



    }
    stages {
        stage('Compile') {
            steps {
            script{
               echo "compiling teh code"
               echo "compiling in ${params.ENV}"}
            }
        }
        stage('UnitTest') {
           when {
              expression{
                 params.EXECUTETEST== true
                }
              }
            steps {
               echo "Test teh code"
            }
        }
        stage('Package') {
            steps {
               echo "Package teh code"
            }
        }
         stage('Example') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
    }
}
