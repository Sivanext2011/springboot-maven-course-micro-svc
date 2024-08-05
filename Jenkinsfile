pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('checkout the code'){
            steps{
                git url:'https://github.com/Sivanext2011/springboot-maven-course-micro-svc.git', branch: 'master'
            }
        }
        stage('build the code'){
            steps{
                sh 'mvn clean package'
            }
        }
}
}

