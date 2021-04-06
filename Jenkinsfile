pipeline {
    agent any
        environment {
            FULL_PATH_BRANCH = "${sh(script:'git name-rev --name-only HEAD', returnStdout: true)}"
            GIT_BRANCH = FULL_PATH_BRANCH.substring(FULL_PATH_BRANCH.lastIndexOf('/') + 1, FULL_PATH_BRANCH.length())
    }
    parameters {
        string(
            name: 'PERSON', 
            defaultValue: 'Mr Jenkins', 
            description: 'Who should I say hello to?')
        string(
            name: 'ANIMALS', 
            defaultValue: 'Mr DONKEY', 
            description: 'Who should I say hello to?')
    }
    stages {
        stage ('developing environment') {
            when {
                expression { $GIT_BRANCH == 'master' }
            }
            steps {
                echo env.GIT_BRANCH
            }
        }
        stage ('staging environment') {
            steps {
                echo "Hello ${params.PERSON}"
            }
        }
        stage ('testing environment') {
            steps {
                sh '''
                env
                echo $GIT_BRANCH
                '''
            }
        }
        
        stage ('prod environment') {
            when {
                branch 'master'
            }
            steps {
                echo env.GIT_BRANCH
                echo $GIT_BRANCH
            }
        }
    }
}
