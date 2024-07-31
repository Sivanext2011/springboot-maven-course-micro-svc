pipeline{
    agent any
    tools{
        maven 'maven-3'
    }
    stages{
        stage('checkout the code'){
            steps{
                git url:'https://github.com/jagdishmodi/springboot-maven-course-micro-svc.git', branch: 'master'
            }
        }
        stage('build the code'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage("sonar quality check"){
            steps{
                script{
                    withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'jenkins-sonar-token') {
                            sh 'mvn sonar:sonar '
                    }

                    timeout(time: 1, unit: 'HOURS') {
                      def qg = waitForQualityGate()
                      if (qg.status != 'OK') {
                           error "Pipeline aborted due to quality gate failure: ${qg.status}"
                      }
                    }

                }  
            }
        }
    }
}
