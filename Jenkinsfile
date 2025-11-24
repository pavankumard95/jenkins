pipeline{
    agent any

    parameters{
        string(name: 'PARAM_STRING', defaultValue: 'random', description: 'This is a string parameter')

    }

    stages{
        stage("Build") {
            steps{
                sh '''
                set +x
                sleep 5
                echo $PARAM_STRING
                '''
            }
        }
        stage("Test") {
            steps{
                sh 'sleep 5'
            }
        }
        stage("Deploy") {
            steps{
                sh 'sleep 5'
            }
        }
    }
}