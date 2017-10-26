node {
	stage('Checkout') {
		checkout scm
	}
	def githubNotifier = load('github-status-notifier')

	try {
		stage('README') {
			sh "cat README.md"
		}
		githubNotifier.success()
	} catch (e) {
		println e.message
		if (e.message.indexOf("code: 201") == -1) {
			currentBuild.result = 'FAILURE'
			try {
				githubNotifier.error('hogehoge')
			} catch (err) {}
		}
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
