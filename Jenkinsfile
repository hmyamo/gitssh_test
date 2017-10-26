node {
	step([$class: 'GitHubSetCommitStatusBuilder'])
	
	stage('Checkout') {
		checkout scm
	}
	//def githubNotifier = load('github-status-notifier')

	stage('README') {
		try {
			sh "cat README.md"
			currentBuild.result = 'SUCCESS'
		} catch (e)
			currentBuild.result = 'FAILURE'
		}
	}
	
	stage('Notify') {
		step([$class: 'GitHubCommitNotifier', resultOnFailure: 'FAILURE'])
	}
	
//		githubNotifier.success()
//  } catch (e) {
//		sh "echo 'catch error'"
//		println e.message
//		println e.responceCode
  	//currentBuild.result = 'FAILURE'
		//githubNotifier.error('hogehoge')
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
