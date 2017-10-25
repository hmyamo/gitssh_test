node {
	stage('Checkout') { checkout scm }
	def githubNotifier = load('github-status-notifier')

	try {
		stage('README') {
			sh "cat README.md"
		}
		githubNotifier.success() | echo "good!"
  } catch (e) {
		sh "echo 'catch error'"
  	//currentBuild.result = 'FAILURE'
		//githubNotifier.error('hogehoge')
 	}
}

// node {
//   step([$class: 'GitHubSetCommitStatusBuilder'])
//
//   stage 'Checkout'
//   checkout scm
//
//   stage 'REAMDE'
//   try {
//     sh "cat README.md"
//     currentBuild.result = 'SUCCESS'
//   } catch (err) {
//     currentBuild.result = 'FAILURE'
//   }
//
//   stage 'Notify'
//   step([$class: 'GitHubCommitNotifier', resultOnFailure: 'FAILURE'])
//
// }
