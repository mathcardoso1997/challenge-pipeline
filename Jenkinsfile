pipeline {
    
    agent any
       
    stages {
      stage('Starting-Job') {
           parameters {
               choice(name: 'CHOICE', choices: ['Redhat', 'Debian'], description: 'Escolha a Distro: ') 
           }
          steps {
              sh '> assessment.txt'
              sh '$DISTRO = "${params.CHOICE}"'
          }
      }
        
      stage('SO-Info') {
          steps {
              sh "echo '====================================' >> assessment.txt"
              sh "echo 'Informacoes do Sistema Operacional:' >> assessment.txt"
              sh "cat /etc/*-release >> assessment.txt"
              echo ""
          }
      }

      stage('Kernel-Info') {
          steps {
              sh "echo '====================================' >> assessment.txt"
              sh "echo 'Informacoes do Kernel:' >> assessment.txt"
              sh "uname -a >> assessment.txt"
              echo ""
          }
      }

      stage('User-Info') {
          steps {
              sh "echo '====================================' >> assessment.txt"
              sh "echo 'Informacoes dos usuarios presentes no sistema:' >> assessment.txt"
              sh "cat /etc/passwd | cut -d: -f1 >> assessment.txt"
              echo ""
          }
      }

      stage('Distro-Info') {
          steps {
              sh "echo '====================================' >> assessment.txt"
              sh "echo 'Distro utilizada no sistema:' >> assessment.txt"
              sh "echo '$DISTRO' >> assessment.txt"
              echo ""
          }
      }

      stage('Package-Info') {
          steps {
              sh "echo '====================================' >> assessment.txt"
              sh "echo 'Informacoes dos pacotes instalado no sistema:' >> assessment.txt"
              sh "dpkg -l >> assessment.txt"
              echo ""
          }
      }
      
    }
    
    post {
        failure {
            echo 'Falha na Compilação'
        }
        success {
            echo 'Compilação finalizada'
        }
    }
    
}
