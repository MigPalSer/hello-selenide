pipeline {

    agent any

    triggers {
        pollSCM '* * * * *'
    }

    stages {


        stage('git') {
            steps {
            
            	sh "echo iniciando pipeline selenoides"
            	
                // Get some code from a GitHub repository
                git url: 'https://github.com/MigPalSer/hello-selenide'
		
            }
        }

 stage('gradle clean') {
            steps {
            
            	sh "./gradlew clean"
		
            }
        }

 stage('gradle assemble') {
            steps {
            
            	sh "./gradlew build"
		
            }
        }

 stage('gradle test') {
            steps {
            
            	sh "./gradlew check"
		
            }
		
        }

    }

post {
        always {
	junit 'build/test-results/test/*.xml'
           jacoco( 
      execPattern: 'build/jacoco/*.exec',
      classPattern: 'build/classes',
      sourcePattern: 'src/main/java',
      exclusionPattern: 'src/test*'
)
	
        }
    }

}
