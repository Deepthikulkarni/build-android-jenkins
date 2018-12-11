node {
  // Mark the code checkout 'stage'....
  stage('Checkout') {
    checkout([
			$class: 'GitSCM',
			branches: [[name: env.BRANCH_NAME]],
			doGenerateSubmoduleConfigurations: false,
			extensions: [], submoduleCfg: [],
			userRemoteConfigs: [[
				name: 'github',
				url: 'https://github.com/Deepthikulkarni/build-android-jenkins.git'
			]]
		])
  }

  stage('Build') {
    //branch name from Jenkins environment variables
    echo "My branch is: ${env.BRANCH_NAME}"
    echo "Building flavor Dolos"
    
    //build your gradle flavor, passes the current build number as a parameter to gradle
    sh "./Dolos/gradlew --stacktrace -PBUILD_NUMBER=${env.BUILD_NUMBER}"
  }
}
