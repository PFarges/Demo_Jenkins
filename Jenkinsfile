pipeline {
    agent { 
        docker { 
            image "python:3.8"
            args '--user 0:0'
        } 

    }
    stages {
        stage('Run schemachange') {
            steps {
                sh "pip install schemachange --upgrade"
                sh "schemachange -f migrations --${SF_CONNECTION} -c ${SF_DATABASE}.SCHEMACHANGE.CHANGE_HISTORY --create-change-history-table"
            }
        }
    }
}