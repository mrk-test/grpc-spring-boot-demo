stage 'Build'
node {
    checkout scm
    def mvnHome = tool 'M3'
    def mvnCommand = "$mvnHome/bin/mvn clean install"
    if (isUnix()) {
        sh mvnCommand
    } else {
        bat mvnCommand
    }
}

stage 'Archive Artifacts'
node {
    archiveArtifacts artifacts: 'grpc-spring-boot-demo-server/target/*.jar', fingerprint: true
}