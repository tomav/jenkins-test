node {

	try {

		setGitHubPullRequestStatus context: 'default', message: 'Build in progress', state: 'INPROGRESS'

	}

	catch (err) {

	setGitHubPullRequestStatus context: 'default', message: 'Build failed', state: 'FAILURE'

	}

	setGitHubPullRequestStatus context: 'default', message: 'Build success', state: 'SUCCESS'

}
