pipeline {

  agent any

  stages {
	  
	//  stage("Defino Nombre proyecto") {  //abro stage
        //    steps {        // abro step
        //        script {  // abro script
	//	def inputConfig
	//		def USER_INPUT = input(
        //            	message: 'Ingrese Nombre Proyecto',
        //            	parameters: [
        //            		string(defaultValue: 'proyecto01',
        //                                    description: 'NombreProyecto',
        //                                    name: 'Config'),
	//		])
		//	salida=$(echo "${USER_INPUT}")
                 //   inputConfig = USER_INPUT
		  
                      
	//	} // cierro script
			
       //     } // cierro step
      //  } //cierro stage
    
	  
	  
	  
	  

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
	   openshift.withProject( 'toolkit' ) {
        echo "Hello from a non-default project: ${openshift.project()}"
    }
 
          }

        }

      }

    }

stage("Interactive_Input") {  //abro stage
            steps {        // abro step
                script {  // abro script
		def inputConfig
			def USER_INPUT = input(
                    	message: 'Ingrese la ruta?',
                    	parameters: [
                    		string(defaultValue: 'https://github.com/mguazzardo/newphp',
                                            description: 'Ruta del git',
                                            name: 'Config'),
			])
		//	salida=$(echo "${USER_INPUT}")
                    inputConfig = USER_INPUT
			
		        openshift.withCluster() {
				
				//openshift.newBuild( inputConfig , "--name=complejo" )  veo que nombre toma por default
				openshift.newBuild( inputConfig )
			}
				 
		   
                      
		} // cierro script
			
            } // cierro step
        } //cierro stage
    


  }

}
