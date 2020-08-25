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

if(buildArchitecture.equals("amd64") || buildArchitecture.equals("both") ) {
 node('boa') {

  def pipeline_descriptor
  def dockerPrivateRegistryForPushes = "${env.DOCKER_REGISTRY_HOST_PORT_FOR_PUSHES}"
  def dockerPrivateRegistryForPulls  = "${env.DOCKER_REGISTRY_HOST_PORT_FOR_PULLS}"
  def componentToBuild
  def buildId
  def imageMetadata
  def archSuffix = "amd64"
  def buildImageTag
  def packageName
  
  pipeline_descriptor = readJSON file: 'build/pipeline/pipeline_descriptor.json'
  componentToBuild = pipeline_descriptor['component']
  // Use Branch Name and Jenkins Build Number as our buildID
  buildId = "${env.BUILD_NUMBER}".toInteger()
  buildId = String.format('%04d',buildId)
  buildId = "${env.BRANCH_NAME}_${buildId}"
  buildId = buildId.replace("_", "-")
  println "Will use a buildId of: ${buildId}."
  imageMetadata = pipeline_descriptor['image.metadata']
  images = []
  buildImageTag = "${buildId}-${archSuffix}"

 }
}
