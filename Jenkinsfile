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
        stage('Build in DEV') { 
          when {
            expression {
              params.ACCOUNT == 'DEV'
            }
          }
            steps {
                sh "echo Building the Project in dev aws account ${env.dev_acc_id}"
            }
        }
        stage('Build in QA ') { 
          when {
            expression {
              params.COLOR == 'QA'
            }
          }
            steps {
                sh "echo Building the Project in QA aws account ${env.qa_acc_id}"
            }
        }
        stage('Deploy') { 
          when {
            expression {
               BRANCH_NAME == /(master|release)/ 
            }
          }
            steps {
               sh 'echo "Deploying on K8S Cluster"'
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
