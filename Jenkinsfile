pipeline {
    agent any
    options { skipDefaultCheckout() }
    environment {
      projectname = "tscout"
    }
    parameters {
        choice(name: 'TARGET_ENVIRONMENT', choices: ['staging'], description: 'Pick something')      
        string(name: 'BRANCHNAME', defaultValue: 'staging', description: 'Please Enter Your Branch Name?')
	string(name: 'ENV01', defaultValue: '', description: 'Please Enter Your ENV01 Name?')
        string(name: 'ENV02', defaultValue: '', description: 'Please Enter Your ENV02 Name?')
        string(name: 'ENV03', defaultValue: '', description: 'Please Enter Your ENV03 Name?')
        string(name: 'ENV04', defaultValue: '', description: 'Please Enter Your ENV04 Name?')
        string(name: 'ENV05', defaultValue: '', description: 'Please Enter Your ENV05 Name?')
        string(name: 'ENV06', defaultValue: '', description: 'Please Enter Your ENV06 Name?')
        string(name: 'ENV07', defaultValue: '', description: 'Please Enter Your ENV07 Name?')
	string(name: 'ENV08', defaultValue: '', description: 'Please Enter Your ENV08 Name?')
	string(name: 'ENV09', defaultValue: '', description: 'Please Enter Your ENV09 Name?')
	string(name: 'ENV10', defaultValue: '', description: 'Please Enter Your ENV10 Name?')		
    }
    stages {
        stage ('staging environment') {
            when { 
                expression { params.BRANCHNAME == 'staging' && params.TARGET_ENVIRONMENT == 'staging'}
            }
            steps {
              sh'''
                    echo "this is staging deployment area"
                    ssh -o "StrictHostKeyChecking=no" ubuntu@tscout-staging bash /home/ubuntu/scripts/graph.sh $BRANCHNAME $ENV01 $BUILD_NUMBER $ENV02 $ENV03 $ENV04 $ENV05 $ENV06 $ENV07 $ENV08 $ENV09 $ENV10

                '''
            }
        }
    }
}

