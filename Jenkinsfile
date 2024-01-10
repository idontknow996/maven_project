pipeline {
    agent any

    parameters {
        string(name: 'ENV', defaultValue: 'DEV', description: 'ENV to compile')
        booleanParam(name: 'executeTest', defaultValue: true, description: 'app version')
        choice(name: 'APP', choices: ['1.0', '1.1', '1.2'], description: 'Pick something')
    }

    stages {
        stage('Compile') {
            steps {
                script {
                    sh "mvn --version"
                    echo "Compile code"
                    echo "Compiling in ${params.ENV} environment"
                    sh "mvn compile"
                }
            }
        }

        stage('Test') {
            when {
                expression {
                    params.executeTest == true
                }
            }
            steps {
                script {
                    echo "Testing"
                    sh "mvn test"
                }
            }
        }

        stage('Package') {
            steps {
                script {
                    echo "Packaging"
                    echo "Packing the app version ${params.APP}"
                    sh "mvn --version"
                    sh "mvn clean package"
                }
            }
        }

        stage('Deployment') {
            input {
                message "Select the version to deploy"
                ok "Version selected"
                parameters {
                    choice(name: "NEWAPP", choices: ["EC2", "ONPrem", "EKS"])
                }
            }
            steps {
                script {
                    echo "Deploy the Code"
                    echo "The deployment platform is ${params.NEWAPP}"
                }
            }
        }
    }
}
