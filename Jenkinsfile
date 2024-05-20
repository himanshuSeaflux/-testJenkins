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
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    def branch = ''
                    switch(params.BUILD_TYPE) {
                        case 'Feature':
                            branch = 'feature-branch-name'
                            break
                        case 'Development':
                            branch = 'development'
                            break
                        case 'Release':
                            branch = 'release-branch-name'
                            break
                        default:
                            branch = 'main'
                            break
                    }
                    echo "Selected BUILD_TYPE: ${params.BUILD_TYPE}"
                    echo "Branch to checkout: ${branch}"
                    // Simulating Git checkout, replace with actual Git checkout if needed
                    sh "echo Checking out branch: ${branch}"
                }
            }
        }

        stage('Build') {
            steps {
                echo "Building for branch based on BUILD_TYPE: ${params.BUILD_TYPE}"
                // Add your build steps here
                sh 'echo Building...'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying build for BUILD_TYPE: ${params.BUILD_TYPE}"
                // Add your deployment steps here
                sh 'echo Deploying...'
            }
        }
    }
}
