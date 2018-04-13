pipeline {
  agent any
  stages {
    stage("checkout") {
      steps {
        echo 'checking out'
        
        checkout([$class: 'GitSCM',
  branches: [[name: '*/master']],
  doGenerateSubmoduleConfigurations: false,
  extensions: [[$class: 'RelativeTargetDirectory',
    relativeTargetDir: 'deploymentversion']],
  submoduleCfg: [],
  userRemoteConfigs: [[url: 'https://github.com/garyli94110/deployment_version.git']]])
      }
    }
  }
}
