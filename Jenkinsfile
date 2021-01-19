def gv

pipeline {
  
  agent any

  parameters {
    
    choice(name: 'VERSION', choices: ['1.1.0','1.2.0','1.3.0'], description: 'A small list of choices')
    
    // booleanParam(name: 'executeTests', defaultValue: true, description: 'Boolean to determine whether or not to execute tests')
    booleanParam(name: 'executeTests', defaultValue: false, description: 'Boolean to determine whether or not to execute tests')

  }

  stages {
    
    stage("initialization") {
      steps {
        script {
          gv = load "script.groovy"
        }
      }
    }

    stage("build") {
      steps {
        
        // echo "Building the application..."

        script {
          gv.buildApp()
        }

      }
    }

    stage("test") {
      
      when {
        expression {
          params.executeTests
        }
      }

      steps {
        // echo "Testing the application..."

        script {
          gv.testApp()
        }

      }
    }

    stage("deploy") {
      
      steps {
        // echo "Deploying the application..."
        // echo "Deploying custom version: ${params.VERSION} "

        script {
          gv.deployApp()
        }

      }

    }
    
  }

}