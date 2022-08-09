pipeline {
    
    agent any


environment {

      sonar_url = 'http://54.209.185.116:9000/'
      sonar_username = 'admin'
      sonar_password = 'muni'
      

 }

    tools {
    jdk 'Java11'
    maven 'Maven 3.6.3'

  }

    stages {
        
        stage('Git Clone') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/kosurumuniraja/achu.git'

            }

        }
        stage('Maven build') {
            steps {
                // Get some code from a GitHub repository
                sh  'mvn clean install -U -Dmaven.test.skip=true'

            }
        }

     stage ('Sonarqube Analysis'){
           steps {
           withSonarQubeEnv('sonarqube') {
           sh '''
           mvn -e -B sonar:sonar -Dsonar.java.source=1.8 -Dsonar.host.url="${sonar_url}" -Dsonar.login="${sonar_username}" -Dsonar.password="${sonar_password}" -Dsonar.sourceEncoding=UTF-8
           '''
           }
         }
      }

}
}


