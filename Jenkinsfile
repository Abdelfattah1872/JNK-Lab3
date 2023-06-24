@Library('my-library') _  
pipeline {
     agent any
    parameters {
        booleanParam(name:'Build', defaultValue: true, description:'')
        choice(name: 'namespace', choices:['Build','clean','push'], description: '' ) 
    }

    stages {
        stage('build') {
            steps {
                buildImage()
            }
        }

        stage('clean') {
            when {
                expression{
                    params.test== true 
                }
            }
            steps {
                cleanUp()
            }
        }
        
        stage('push') {  
            steps {
               pushImage()
            }
        }    
    }

     post {
        always { 
            echo 'job was triggered'
        }
        success {
            echo 'your app is deployed successfully'
        }
        failure {
            echo 'dyploying failure'
        }

}
}