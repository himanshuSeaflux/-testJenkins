pipeline {
    agent any
   // parameters { 
   //    choice(name: 'BUILD_TYPE', choices: ['Feature', 'Development','Release'], description: 'Select the type of branch to build')
   //   // string(name: 'SELECTED_BRANCH', defaultValue: '', description: 'Enter the feature branch name or give "development" if you want to promote Image to higher Environments ') 
   //    gitParameter branchFilter: 'origin./(.)', defaultValue: 'development', name: 'BRANCH', type: 'PT_BRANCH',description: 'Select the branch to Build from the Dropdown List'
   //    string(name: 'REBUILD_IMAGE_TAG', defaultValue: '', description: 'Enter the image tag to check in the database')
   //  }
 parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'main', name: 'BRANCH', type: 'PT_BRANCH'
  }
    stages {
        stage('Example') {
            steps {
                echo "Choice: ${params.TAG_VERSION}"
                sh "echo Choice: ${params.TAG_VERSION}"
                sh 'echo Choice: $TAG_VERSION'
                echo "Choice Branch: ${params.TAG_VERSION}"
            }
        }
    }
}
