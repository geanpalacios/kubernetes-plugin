def buildNumber = BUILD_NUMBER as int; if (buildNumber > 1) milestone(buildNumber - 1); milestone(buildNumber) // JENKINS-43353 / JENKINS-58625
node('docker') {
    checkout scm
    withEnv(["WSTMP=${pwd tmp: true}"]) {
        try {
            sh 'bash kind.sh'
        } finally {
            if (fileExists("$WSTMP/kindlogs/docker-info.txt")) {
                archiveArtifacts "$WSTMP/kindlogs"
            }
        }
    }
}
