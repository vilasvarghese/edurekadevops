pipeline {
    agent { label 'master' }
    tools { 
        maven 'mymaven' 
    }
    stages {
	stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }    
        stage('scm') {
            steps {
                git 'https://github.com/vilasvarghese/edurekadevops.git'
            }
        }

    stage('build') {
        steps {
            sh 'mvn clean install'
        }
    }
    stage('deploy') {
        steps {
		    sh 'cp /var/lib/jenkins/workspace/declarativepipeline/target/*.war /opt/tomcat/webapps/'
        }
    }
}
}