pipeline 
{
    agent any
    
    stages 
    {
        stage('Compile') 
        {
            steps
            {
                // Get some code from a GitHub repository
                //git 'https://github.com/jglick/simple-maven-project-with-tests.git'
                echo "Hello Jenkins"
                // Run Maven on a Unix agent.
                //sh "mvn -Dmaven.test.failure.ignore=true clean package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
        stage('Test')
        {
            steps
            {
                echo "Testing"
            }
        }
        stage('package')
        {
            steps
            {
                echo "Packaging"
            }
        }
    }
}
