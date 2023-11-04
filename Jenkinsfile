pipeline {
    agent any

    environment {
        SSH_CRED = credentials('SSH_CRED')
    }
   // parameters {
    //    string(name: 'COMPONENT', defaultValue: 'mongodb', description: 'Enter the Component Name')
    //    choice(name: 'CHOICE', choices: ['dev', 'prod'], description: 'Choose the Environment'))
   // }
   stages {
        stage('Lint Checks') {                  // This stage should only be executed when you run job from feature branch
            steps {
                sh '''
                    echo *** Starting Lint Checks ***
                    echo *** Lint Checks Completed ***
                '''
            }
        }
          stage('Performing a dry run') {       //  This stage should only run when there is a pull request
            steps {
                sh '''
                    env
                    ansible-playbook robo-dryrun.yml -e ENV=dev -e COMPONENT=mongodb -e ansible_user=${SSH_CRED_USR} -e ansible_password=${SSH_CRED_PSW}
                '''
            }
       }
   }
}