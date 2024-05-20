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


def branchType = params.BRANCH_TYPE
def branchName = params.BRANCH_NAME

stage('Checkout Code') {
  steps {
    script {
      // Define empty list to store filtered branches
      def filteredBranches = []
      
      // Get all branches using 'git branch -lr' command
      def allBranches = sh(script: 'git branch -lr', returnStdout: true).trim().split("\n")
      
      // Filter branches based on Branch Type
      if (branchType == 'feature') {
        filteredBranches = allBranches.findAll { branch -> branch.startsWith('feature/') }
      } else if (branchType == 'release') {
        filteredBranches = allBranches.findAll { branch -> branch.startsWith('release/') }
      }
      
      // Display filtered branches in the console log (optional)
      echo "Available ${branchType} branches:"
      filteredBranches.each { branch ->
        echo "* ${branch}"
      }
      
      // Select the specific branch name (optional, user can choose from UI)
      if (branchName) {
        git branch: branchName
      } else {
        // Handle scenario where no specific branch name is chosen
        error "Please select a specific branch name from the Branch Name parameter."
      }
    }
  }
}
