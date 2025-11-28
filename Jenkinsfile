pipeline{
    agent any

    // parameters{
    //     string(name: 'PARAM_STRING', defaultValue: 'random', description: 'This is a string parameter')
    //     text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
    //     booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
    //     choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
    //     password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    // }
    // triggers{
    //     cron('*/59 * * * *')
    // }

    stages{
        stage('Checkout'){
            steps{
                git branch: 'main', credentialsId: 'f07ab0e7-3a48-4ae8-89a7-94d5d291b0d3', url: 'https://github.com/pavankumard95/jenkins.git' 
            }
        }
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
                script {
                    echo "${params.BIOGRAPHY}"
                }
            }
        }
        stage("Deploy") {
            steps{
                sh 'sleep 5'
            }
        }
    }
}