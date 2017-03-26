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