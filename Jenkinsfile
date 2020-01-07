pipeline {
    agent any
     
    stages { 
      stage('Ansible Init') {
        steps {
          script {
            def tfHome = tool name: 'Ansible'
            env.PATH = "${tfHome}:${env.PATH}"
            sh 'ansible --version'          
           }
          }
        }       
        stage('Ansible Deploy') {     
          steps {      
            dir('dev/ansible') {
              sh 'ansible all -m ping -i hosts'  
            }
          }
        }
     }
}
