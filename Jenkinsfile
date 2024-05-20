// pipeline {
//     agent any
//    // parameters { 
//    //    choice(name: 'BUILD_TYPE', choices: ['Feature', 'Development','Release'], description: 'Select the type of branch to build')
//    //   // string(name: 'SELECTED_BRANCH', defaultValue: '', description: 'Enter the feature branch name or give "development" if you want to promote Image to higher Environments ') 
//    //    gitParameter branchFilter: 'origin./(.)', defaultValue: 'development', name: 'BRANCH', type: 'PT_BRANCH',description: 'Select the branch to Build from the Dropdown List'
//    //    string(name: 'REBUILD_IMAGE_TAG', defaultValue: '', description: 'Enter the image tag to check in the database')
//    //  }
//  parameters {
//     // choice(name: 'BUILD_TYPE', choices: ['Feature', 'Development','Release','main'], description: 'Select the type of branch to build')
//     gitParameter branchFilter: '*', defaultValue: 'main', name: 'BRANCH', type: 'PT_BRANCH'
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


// pipeline {
//   agent any
//   parameters {
//     choice(name: 'BUILD_TYPE', choices: ['Feature', 'Development','Release','main'], description: 'Select the type of branch to build')
//     gitParameter branchFilter: 'origin.*/(.*)', defaultValue: 'main', name: 'BRANCH', type: 'PT_BRANCH'
//     // gitParameter branchFilter: 'origin/Feature/.*', defaultValue: 'main', name: 'BRANCH', type: 'PT_BRANCH'
//   }
//   stages {
//     stage('Example') {
//        steps {
//                 echo "Choice: ${params.BRANCH}"
//                 sh "echo Choice: ${params.BRANCH}"
//                 sh 'echo Choice: $BRANCH'
//                 echo "Choice Branch: ${params.BRANCH}"
//             }
//     }
//   }
// }



pipeline {
    agent any

    parameters {
        // Define the build type choice parameter
        choice(name: 'BUILD_TYPE', 
               choices: ['Feature', 'Development', 'Release', 'main'], 
               description: 'Select the type of branch to build')

        // Define the Git parameter with a branch filter
        gitParameter(name: 'BRANCH', 
                     type: 'PT_BRANCH', 
                     defaultValue: 'main', 
                     branchFilter: 'origin/.*', 
                     selectedValue: 'DEFAULT', 
                     useRepository: 'https://github.com/himanshuSeaflux/testJenkins.git')
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Get the selected branch from parameters
                    def selectedBranch = params.BRANCH

                    // Checkout the selected branch
                    checkout([$class: 'GitSCM',
                              branches: [[name: "*/${selectedBranch}"]],
                              userRemoteConfigs: [[url: 'https://github.com/himanshuSeaflux/testJenkins.git']]])
                }
            }
        }

        stage('Build') {
            steps {
                echo "Building branch: ${params.BRANCH} of type: ${params.BUILD_TYPE}"
                // Add your build steps here
            }
        }
    }
}
