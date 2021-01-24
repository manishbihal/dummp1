node {
    
    stage('Checkout SCM') {
        git branch: 'dev', credentialsId: 'githubs', url: 'https://github.com/atinsingh/dummp1.git'
    }
    stage('Compile ') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         sh 'mvn compile'
        }
    }
    stage('Unit Test') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         sh 'mvn Test'
        }
    }
    stage('Publish Test Result') {
        junit '**/*.xml'
    }
    stage('Package') {
        withMaven(jdk: 'jdk8', maven: 'm363') {
         sh 'mvn package'
        }
    }
    stage('Publish Artifact') {
        archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
    }
}
