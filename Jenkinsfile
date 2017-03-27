stage 'Build'
node {
    checkout scm
    def mvnHome = tool 'M3'
    def mvnCommand = "$mvnHome/bin/mvn clean install -DskipTests"
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

stage 'Deploy'
node {
    configFileProvider([configFile(fileId: 'my-settings-xml', variable: 'mavenSettings')]) {
        def mvnHome = tool 'M3'
        def mvnCommand = "$mvnHome/bin/mvn -s $mavenSettings deploy"
        if (isUnix()) {
            sh mvnCommand
        } else {
            bat mvnCommand
        }
    }
}