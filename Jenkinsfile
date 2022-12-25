pipeline {
    agent any
     stages {
      stage('checkout') {
           steps {
             
                git branch: 'main', url: 'https://github.com/MusthafaMashkura/jenkins-cicd-ansible.git'
             
          }
        }
      stage('Build') {
           steps {
               sh 'mvn clean test package'
            }
        }
      stage('Check Ansible version') {
          agent {label 'ANSIBLE'}
                options {
                timeout(time: 1, unit: 'HOURS')
                }
          steps {
               sh 'ansible --version'
               sh 'python --version'
            }
        }
      stage('Ansible Deploy') {
          agent {label 'ANSIBLE'}
                options {
                timeout(time: 1, unit: 'HOURS')
                } 
          sshagent(['app-server']) {
            sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-52-90-61-49.compute-1.amazonaws.com:/opt/apache-tomcat-8.5.38/webapps/'
        }
          
           steps {
               sh 'ls -ltrh'
               sh 'ansible-playbook -i localhost myfirstplaybook.yml'
            }
        }
    }
/*    post { 
        always { 
            cleanWs()
        }
    }*/
}
