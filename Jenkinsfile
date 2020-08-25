properties([parameters([choice(choices: ['amd64', 'ppc64le', 'both'], description: 'Specify whether Docker images should be created for amd64 (x86_64) or ppc64le architectures or for both architectures.', name: 'BuildArchitecture')])])

def buildArch = params.BuildArchitecture
println "${buildArch}"
  echo sh(returnStdout: true, script: 'env')

