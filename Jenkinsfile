pipeline {

  agent any

  stages {

    stage('Build') {


      steps {

        script {

          openshift.withCluster() {

	    // Saludamos desde el cluster
            openshift.withProject( 'openshiftcluster' ) {
        echo "Hola desde el  proyecto ${openshift.project()} en el cluster ${openshift.cluster()}"
        proyecto=openshift.project()
        echo "El proyecto se llama $proyecto"
    }
	   openshift.withProject( 'newphp' ) {
        echo "Hello from a non-default project: ${openshift.project()}"
    }
 
          }

        }

      }

    }

stage("Interactive_Input") {
            steps {
                script {
		def inputConfig
			def USER_INPUT = input(
                    	message: 'Ingrese la ruta?',
                    	parameters: [
                    		string(defaultValue: 'None',
                                            description: 'Path of config file',
                                            name: 'Config'),
			])
			echo "salida es: ${USER_INPUT}"
			def build = ${USER_INPUT}
			echo "el build es: $build"
                }
			
            }
        }
    


  }

}
