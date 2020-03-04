pipeline {
   agent any
   parameters {
        string(defaultValue: "TEST", description: 'What environment?', name: 'userFlag')
        choice(choices: ['US-EAST-1', 'US-WEST-2'], description: 'What AWS region?', name: 'region')
    }
     
    stages {
     stage("foo") {
       steps {
          echo "flag: ${params.userFlag}"
          echo "region: ${params.region}"
       }
      }
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
