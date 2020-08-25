properties([parameters([choice(choices: ['amd64', 'ppc64le', 'both'], description: 'Specify whether Docker images should be created for amd64 (x86_64) or ppc64le architectures or for both architectures.', name: 'BuildArchitecture')])])

def buildArch = params.BuildArchitecture
println "${buildArch}"

def multiArchManifests = "no"


node('master') {
 stage('Git Checkout') {
    echo sh(returnStdout: true, script: 'env')
    deleteDir() /* clean up our workspace */
    checkout scm
    stash name: "boa-git-sources", excludes: ".git/**"
    // Set executable permissions on all shell scripts
    sh script: "find ${env.WORKSPACE} -type f -iname \"*.sh\" -exec chmod +x {} \\;" , returnStdout: true

 }
}
