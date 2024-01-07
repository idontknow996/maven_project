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
        // Get some code from a GitHub repository
        //git 'https://github.com/jglick/simple-maven-project-with-tests.git'
        //echo "Hello Jenkins"
        // Run Maven on a Unix agent.
        //sh "mvn -Dmaven.test.failure.ignore=true clean package"

        // To run Maven on a Windows agent, use
        // bat "mvn -Dmaven.test.failure.ignore=true clean package"
        script {
          echo "Compile code"
          echo "Compiling in ${params.ENV} environment"
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
        }
      }
    }
  }

  stage('package') {
    steps {
      script {
        echo "Packaging"
        echo "packing the app version ${params.APP}"
      }

    }
  }
}