pipeline {
    agent any 
    environment {
        dev_acc_id = "1822635192192"
        qa_acc_id = "18226351193193"
    }
    parameters {
        choice(name: 'ACCOUNT', choices: ['DEV', 'QA'], description: 'Pick AWS ACCOUNT')
    }
    stages {
        stage('Deploy in DEV') { 
          when {
            expression {
              params.ACCOUNT == 'DEV'
            }
          }
            steps {
                sh "echo Building the Project in dev aws account ${env.dev_acc_id}"
            }
        }
        stage('Deploy in QA ') { 
          when {
            expression {
              params.ACCOUNT == 'QA'
            }
          }
            steps {
                sh "echo Building the Project in QA aws account ${env.qa_acc_id}"
            }
        }
    }
    post { 
        always { 
            echo 'Deleting Workspace'
            deleteDir() /* clean up our workspace */
        }
    }
}



