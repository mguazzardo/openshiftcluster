pipeline {

  agent any

  stages {

    stage('Build') {


      steps {

        script {

          openshift.withCluster() {

	    // Saludamos desde el cluster
            openshift.withProject( 'myproject' ) {
        echo "Hola desde el  proyecto ${openshift.project()} en el cluster ${openshift.cluster()}"
    } 
          }

        }

      }

    }

  }

}
