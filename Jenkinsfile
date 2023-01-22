pipeline {
    agent any 
    environment {
        //dev_acc_id = "1822635192192"
        //qa_acc_id = "18226351193193"
        my_account = "${params.ACCOUNT_NAME}"
    }
    parameters {
        choice(name: 'ACCOUNT_NAME', choices: ['DEV', 'QA'], description: 'Pick AWS ACCOUNT')
    }
    stages {
        stage('Deploy in DEV') { 
          when {
            expression {
              params.ACCOUNT_NAME == 'DEV'
            }
          }
            steps {
                sh "echo Building the Project in dev aws account."
                getAccountNumber(env.my_account)

            }
        }
        stage('Deploy in QA ') { 
          when {
            expression {
              params.ACCOUNT_NAME == 'QA'
            }
          }
            steps {
                sh "echo Building the Project in QA aws account."
                getAccountNumber(env.my_account)
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



def getAccountNumber(String Acc_name) {

    if (Acc_name == 'DEV') {
        sh "echo Hello from function name  getAccountNumber, FYI DEV Aws Account ID"
        sh "echo DEV_ACC_ID = 1822635192192"
    }  else {
         sh "echo Hello from function name  getAccountNumber, , FYI QA Aws Account ID"
         sh "echo QA_ACC_ID = 1822635193193"
    }
}
