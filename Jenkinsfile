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
			//install will copy the war to the .m2 folder.
        }
    }
    stage('deploy') {
        steps {
		    sh 'cp /var/lib/jenkins/.m2/repository/com/edureka/devops/edurekadevops/*.war /opt/tomcat/webapps/'
        }
    }
}
}