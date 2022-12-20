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
           steps {
               sh 'ls -ltrh'
               sh 'ansible-playbook -i localhost myfirstfile.yml'
            }
        }
    }
/*    post { 
        always { 
            cleanWs()
        }
    }*/
}
