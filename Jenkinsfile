pipeline {
    agent any 
    parameters {
        choice(name: 'NAME', choices: ['One', 'Two', 'Three'], description: 'Pick NAME')
        choice(name: 'LASTNAME', choices: ['HELLO', 'MOTO', 'FELLO'], description: 'Pick LASTNAME')
        choice(name: 'SHOW', choices: ['true', 'false'], description: 'Pick SHOW')
    }
    stages {
        stage('Build') { 
            steps {
                sh 'echo "Build stage executing shell script my_fst_jenkins.sh"'
                sh 'chmod +x my_fst_jenkins.sh'
                sh "./my_fst_jenkins.sh ${params.NAME} ${params.LASTNAME} ${params.SHOW}"
            }
        }
        stage('Test') { 
            steps {
                sh 'echo "Running Test scripts from QA team"'
            }
        }
        stage('Deploy') { 
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
