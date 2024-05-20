// pipeline {
//     agent any
//    // parameters { 
//    //    choice(name: 'BUILD_TYPE', choices: ['Feature', 'Development','Release'], description: 'Select the type of branch to build')
//    //   // string(name: 'SELECTED_BRANCH', defaultValue: '', description: 'Enter the feature branch name or give "development" if you want to promote Image to higher Environments ') 
//    //    gitParameter branchFilter: 'origin./(.)', defaultValue: 'development', name: 'BRANCH', type: 'PT_BRANCH',description: 'Select the branch to Build from the Dropdown List'
//    //    string(name: 'REBUILD_IMAGE_TAG', defaultValue: '', description: 'Enter the image tag to check in the database')
//    //  }
//  parameters {
//     choice(name: 'BUILD_TYPE', choices: ['Feature', 'Development','Release'], description: 'Select the type of branch to build')
//     gitParameter branchFilter: 'origin/(.*)', defaultValue: 'main', name: 'BRANCH', type: 'PT_BRANCH'
//   }
//     stages {
//         stage('Example') {
//             steps {
//                 echo "Choice: ${params.BRANCH}"
//                 sh "echo Choice: ${params.BRANCH}"
//                 sh 'echo Choice: $BRANCH'
//                 echo "Choice Branch: ${params.BRANCH}"
//             }
//         }
//     }
// }


pipeline {
    agent any 
    parameters {
        choice(name: 'BUILD_TYPE', choices: ['Feature', 'Development', 'Release'], description: 'Select the type of branch to build')
        gitParameter branchFilter: 'origin/(.*)', defaultValue: 'main', name: 'BRANCH', type: 'PT_BRANCH'
    }
    stages {
        stage('Checkout') {
            steps {
                script {
                    def selectedBranch = params.BUILD_TYPE == 'Feature' ? 'origin/feature/*' :
                                        params.BUILD_TYPE == 'Development' ? 'origin/develop/*' :
                                        'origin/release/*'
                    
                    checkout([
                        $class: 'GitSCM', 
                        branches: [[name: selectedBranch]],
                        doGenerateSubmoduleConfigurations: false,
                        extensions: [],
                        submoduleCfg: [],
                        userRemoteConfigs: [[url: 'https://your-repo-url.git']]
                    ])
                }
            }
        }
        stage('Build') {
            steps {
                echo "Building branch: ${params.BRANCH}"
                // Add your build steps here
            }
        }
    }
}
