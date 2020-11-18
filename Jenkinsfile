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

                    // Variables for input
                    def inputGit

                    //def inputTest

                    // Get the input
                    def userInput = input(
                            id: 'userInput', message: 'Enter path of test reports:?',
                            parameters: [

                                    string(defaultValue: 'None',
                                            description: 'Path of config file',
                                            name: 'Git'),
                                    //string(defaultValue: 'None',
                                    //        description: 'Test Info file',
                                    //        name: 'Test'),
                            ])

                    // Save to variables. Default to empty string if not found.
                    inputConfig = userInput.Git?:''
                    //inputTest = userInput.Test?:''



                    // Echo to console
                    echo("Ruta: ${inputGit}")

                    // Write to file
                    writeFile file: "inputData.txt", text: "Config=${inputConfig}\r\nTest=${inputTest}"

                    // Archive the file (or whatever you want to do with it)
                    archiveArtifacts 'inputData.txt'
                }
            }
        }
    


  }

}
