pipeline { 
    agent { label 'MAVEN_JDK8'}
    stages {
        stage('VCS') {
            steps {
                git url: 'https://github.com/sridhar231/game-of-life.git',
                    branch: 'declarative'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }
        stage('artifact') {
           steps {
            archiveArtifacts artifacts: '**/target/gameoflife.war'
            junit testResults: '**/surefire-reports/TEST-*.xml'
           }
       }
    }
}