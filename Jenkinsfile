def stageStatus = 'Failed'
pipeline{
    agent any

    //parameters{
    //       string(name: 'PARAM_STRING', defaultValue: 'SUCCESS', description: 'This is a string parameter')
    //     text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
    //     booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    //     choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    //     password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    //}
    // triggers{
    //     cron('*/59 * * * *')
    // }

    stages{
        stage('Checkout'){
            steps{
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/pavankumard95/jenkins.git' 
            }
        }
        stage("Build") {
            steps{
                sh '''
                ls -lrt
                '''
                script{
                stageStatus = 'Success'
                }
            }
        }
        parallel{
        stage("Test") {
            when {
                expression{
                    stageStatus == 'Success'
                }
            }
            steps{
                 echo 'Cleaning up build.'
                /*script {
                    try{
                        sh 'exit 1'
                        echo "In Test stage"
                        stageStatus = 'Failed'
                        echo "Stage status:${stageStatus}"
                    }
                    catch (Exception e) {
                        echo "Tests failed with error: ${e.getMessage()}"
                        currentBuild.result = 'UNSTABLE'
                        
                    } finally {
                        echo 'Cleaning up build.'
                }*/
            }
        }
        stage('Run Tests') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                    sh 'exit 0'
                }
            }
        }}
        stage("Deploy") {
            steps{
                sh 'sleep 5'
                echo "Deploying build"
            }
        }
    }
}
