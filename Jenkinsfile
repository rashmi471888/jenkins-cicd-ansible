pipeline {
    agent ANSIBLE
    tools { 
        maven 'mymaven' 
        jdk 'myjdk' 
    }
     
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
           steps {
               sh 'ansible --version'
               sh 'python --version'
            }
        }
      stage('Ansible Deploy') {
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
