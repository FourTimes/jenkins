pipeline {
    agent any
        environment {
        PasswordId     = credentials('password')
        UsernameId     = credentials('username')
    }
    parameters {
        choice(
            choices: ['select', 'dev' , 'test', 'prod'],
            description: 'Mention the target environment',
            name: 'REQUESTED_ACTION')
    }
    stages {
        stage ('NO TARGET') {
            when {
                expression { params.REQUESTED_ACTION == 'select' }
            }
            steps {
                echo "PLEASE PASS TARGET NAME"
            }
        }
        stage ('DEVELOPMENT') {
            when {
                expression { params.REQUESTED_ACTION == 'dev' }
            }
            steps {
                sshpass -p $PasswordId rsync -rvz -e 'ssh -o StrictHostKeyChecking=no -p 22' --progress *  node@13.82.230.104:/home/node/hard/
            }
        }
        stage ('TEST') {
            when {
                expression { params.REQUESTED_ACTION == 'test' }
            }
            steps {
                sshpass -p $PasswordId rsync -rvz -e 'ssh -o StrictHostKeyChecking=no -p 22' --progress *  node@13.82.230.104:/home/node/hard/
            }
        }
        stage ('PRODUCTION') {
            when {
                expression { params.REQUESTED_ACTION == 'prod' }
            }
            steps {
                sshpass -p $PasswordId rsync -rvz -e 'ssh -o StrictHostKeyChecking=no -p 22' --progress *  node@13.82.230.104:/home/node/hard/
            }
        }
    }
}