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
    stage("parseVersion") {
      steps {
          sh 'grep BUILD_VERSION ./deploymentversion/payroll_iop_master_deploy.properties | cut -d= -f2 > BUILD_VERSION'
          sh 'grep BUILD_RELEASE ./deploymentversion/payroll_iop_master_deploy.properties | cut -d= -f2 > BUILD_RELEASE'
          sh 'grep VERTEX_RELEASE_VERSION ./deploymentversion/payroll_iop_master_deploy.properties | cut -d= -f2 > VERTEX_RELEASE_VERSION'
      }
    }
  }
}
