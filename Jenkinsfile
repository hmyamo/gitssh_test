node {
	stage('Checkout') { checkout scm }
	def githubNotifier = load('github-status-notifier')

	try {
		stage('README') {
			sh "cat README.md"
		}
		githubNotifier.success()
  } catch (e) {
  	//currentBuild.result = 'FAILURE'
		githubNotifier.error('hogehoge')
 	}
}
