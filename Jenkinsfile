pipeline { 
    agent { label 'MAVEN_JDK8'}
    tools { jdk 'JDK_8_UBUNTU'}
    triggers { cron('* * * * *') }
    parameters { choice(name: 'MAVEN_GOAL', choices: ['package', 'install', 'clean'], description: 'Maven Goal') }
    stages {
        stage('VCS') {
            steps {
                git url: 'https://github.com/sridhar231/game-of-life.git',
                    branch: 'declarative'
            }
        }
        stage('build') {
            steps {
                sh "mvn ${params.MAVEN_GOAL}"
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