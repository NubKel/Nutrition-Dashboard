pipeline {
    
    agent any
    
    options { 
        disableConcurrentBuilds() 
        timeout(time: 1, unit: 'HOURS')
    }
    
    // environment {
        
    // }
    
    // parameters {
    //             string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        
    //             text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        
    //             booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        
    //             choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        
    //             password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    // }

    stages {

        stage('Example credential stage') {
            environment {
                SERVICE_CREDS = credentials('83243253-92af-4166-9985-308b47c6bdc1')
            }
            steps {
                sh 'echo "The secret is $SERVICE_CREDS"'
            }
        }
        
        // stage('Example parameters') {
        //     steps {
        //         echo "Hello ${params.PERSON}"

        //         echo "Biography: ${params.BIOGRAPHY}"

        //         echo "Toggle: ${params.TOGGLE}"

        //         echo "Choice: ${params.CHOICE}"

        //         echo "Password: ${params.PASSWORD}"
        //     }
        // }


        stage('Starting the service...') {
//             input {
//                 message "The process might take a while, should we continue?"
//                 ok "Yes."
//             }
            steps {
//                 sh '/home/ubuntu/.nvm/versions/node/v16.15.1/bin/npm start'
                sh 'curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash'
                sh 'nvm install 14.4.0'
                sh 'yarn start'
            }
        }
    }
    
    post { 
        failure { 
            echo 'Something went wrong, unable to start the service!'
        }
    }

}
