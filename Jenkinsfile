pipeline {
    agent {label 'linux_slave2'}
 environment {
        // Declare tool installations
                maven 'mymaven'
                jdk 'myjdk'

        JDK_HOME = tool name: 'jdk-17', type: 'jdk'
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
            script{
               
               echo "compiling in ${params.ENV}"}
               sh 'mvn compile'
            }
        }
        stage('UnitTest') {
           when {
              expression{
                 params.EXECUTETEST== true
                }
              }
            steps {

               script
               {echo "Test teh code"
               sh 'mvn test'}
            }
        }
        stage('Package') {
            steps {
                script{
               echo "Package teh code"
               sh 'mvn package'}
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
                echo "Hello, ${PERSON}, nice to meet you."
            }
        }
    }
}
