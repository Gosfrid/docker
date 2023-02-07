pipeline {
    agent any
    parameters {
        booleanParam(name: 'Refresh',
                    defaultValue: false,
                    description: 'Read Jenkinsfile and exit.')
		    }
    stages {
        // stage('Pre') { hello push
        //     steps {
        //         sh 'ansible-playbook -v -i /home/jenkins/.jenkins/workspace/FlaskApp/inventory.yaml /home/jenkins/.jenkins/workspace/FlaskApp/playbook.yaml'
        //     }
        // }
        // stage('Test') { 
        //     steps {
        //         sh 'sudo pytest /home/jenkins/.jenkins/workspace/FlaskApp/'
        //     }
        // }
        stage('Unit Tests') {
            steps {
                sh '''
                      python3 -m pytest ./prime/tests/test_unit.py
                      python3 -m pytest ./converter/tests/test_unit.py
                      python3 -m pytest ./main/tests/test_unit.py
                   '''
            }
        }
        stage('docker prune') {
            steps {
                sh 'docker system prune -a -f'
            }
        }

        stage('docker compose') {
            steps {
                sh 'docker-compose build'
            }
        }

        // stage('connect via ssh deploy server and run app') {
        //     steps {
        //         sh '''
        //            #!/bin/bash
        //            ssh -i /home/jenkins/.ssh/training.pem -o StrictHostKeyChecking=no ubuntu@10.1.1.10 << EOF
        //            docker system prune -a -f
        //            docker-compose -f /home/ubuntu/API2/docker-compose.yaml up -d
        //         '''
        //     }
        // }

        // stage('connect via ssh deploy server and run app') {
        //     steps {
        //         sh '''
        //            #!/bin/bash
        //            ssh -i /home/jenkins/.ssh/training.pem -o StrictHostKeyChecking=no ubuntu@10.1.1.10 << EOF
        //            docker system prune -a -f
        //            docker-compose -f /home/ubuntu/API2/docker-compose.yaml up -d
        //         '''
        //     }
        // }
        
    }
}
