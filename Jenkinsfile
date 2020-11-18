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
		def userInput = input(
                            id: 'userInput', message: 'Enter path of test reports:?',
                           

                                    string(defaultValue: 'None',
                                            description: 'Path of config file',
                                            name: 'Config'),)
				
			    inputConfig = Config?:''


                }
            }
        }
    


  }

}
