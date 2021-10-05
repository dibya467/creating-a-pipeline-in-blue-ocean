pipeline {
  agent none
  stages {
    stage('Stage') {
      parallel {
        stage('Test_Stage') {
          agent any
          steps {
            echo 'Hello Step of Stage'
          }
        }

        stage('Func_Test_Stage') {
          agent {
            node {
              label '"host-func"'
            }

          }
          steps {
            sleep(time: 100, unit: 'MILLISECONDS')
          }
        }

        stage('Func_Stage2') {
          steps {
            catchError()
            timeout(time: 10) {
              echo 'Working'
            }

          }
        }

      }
    }

    stage('Alpha_Stage') {
      steps {
        node(label: '"host_alpha1"')
      }
    }

  }
}