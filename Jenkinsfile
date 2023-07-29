pipeline{
    agent none
    tools{
        maven "maven"
    }
    stages{
        stage("Fetch code from github repo qprofiles"){
agent any
            steps{
                git url: "https://github.com/lavanyakk9954/car-api-project.git"
                echo 'first job done'
            }
        }
        stage("This is to compile the code"){
agent{
label 'slave1'
}
            steps{
                sh 'mvn compile'
                recordIssues(tools: [pmdParser()])
            }
        }
        stage("This is to test the code."){
agent{
label 'slave1'
}
            steps{
                sh 'mvn test'
            }
        }
        stage("This is QA testing"){
agent{
label 'slave2'
}
            steps{
                sh 'mvn pmd:pmd'
            }
        }
        stage("This is to set the package of a code"){
agent{
label 'slave2'
}
            steps{
                sh 'mvn package'
            }
        }
    }
}
