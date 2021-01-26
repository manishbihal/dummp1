node('awsLinux') {
    stage('Checkout SCM'){
        git branch: 'dev', credentialsId: 'gitToken', url: 'https://github.com/manishbihal/dummp1.git'
    }
    stage('Compile'){
        withMaven(jdk: 'Java8', maven: 'M363') {
        sh 'mvn compile'
        }
    }
    stage('Unit Test'){
        withMaven(jdk: 'Java8', maven: 'M363') {
        sh 'mvn test'
        }
    }
    stage('Publish Test Results'){
        junit '**/*.xml'
    }
    stage('Packge'){
         withMaven(jdk: 'Java8', maven: 'M363') {
        sh 'mvn package'
        }
    }
    stage('Publish Artifact'){
        archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
    }
}
