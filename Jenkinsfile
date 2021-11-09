pipeline {
    
    agent any
    
    stages {
      stage('Starting-Job') {
        sh 'echo > assessment.txt'
      }
        
      stage('SO-Info') {
          steps {
              sh "echo '====================================' >> assessment.txt"
              sh "echo 'Informacoes do Sistema Operacional: (( ${hostname -i} )) ' >> assessment.txt"
              sh "cat /etc/*-release >> assessment.txt"
              echo ""
          }
      }

      stage('Kernel-Info') {
          steps {
              sh "echo '====================================' >> assessment.txt"
              sh "echo 'Informacoes do Kernel: (( ${hostname -i} ))' >> assessment.txt"
              sh "uname -a >> assessment.txt"
              echo ""
          }
      }

      stage('User-Info') {
          steps {
              sh "echo '====================================' >> assessment.txt"
              sh "echo 'Informacoes dos usuarios presentes no sistema: (( ${hostname -i} ))' >> assessment.txt"
              sh "cat /etc/passwd | cut -d: -f1 >> assessment.txt"
              echo ""
          }
      }

      stage('Distro-Info') {
          steps {
              sh "echo '====================================' >> assessment.txt"
              sh "echo 'Distro utilizada no sistema: (( ${hostname -i} ))' >> assessment.txt"
              sh "echo '$DISTRO' >> assessment.txt"
              echo ""
          }
      }

      stage('Package-Info') {
          steps {
              sh "echo '====================================' >> assessment.txt"
              sh "echo 'Informacoes dos pacotes instalado no sistema: (( ${hostname -i} ))' >> assessment.txt"
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
