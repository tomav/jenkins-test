node {

    step([
            $class       : 'GitHubPRStatusBuilder',
            statusMessage: [
                    content: "Build #${env.BUILD_NUMBER} started"
            ]
    ])

    setGitHubPullRequestStatus context: 'build', state: 'PENDING', message: 'Waiting for build...'
    setGitHubPullRequestStatus context: 'test', state: 'PENDING', message: 'Waiting for testing...'
    setGitHubPullRequestStatus context: 'deploy', state: 'PENDING', message: 'Waiting for deployment...'

    stage "build"
    try {
        sh('sleep 5')
        setGitHubPullRequestStatus context: 'build', state: 'SUCCESS', message: 'Build successful'
    } catch (error) {
        setGitHubPullRequestStatus context: 'build', state: 'FAILURE'
        setGitHubPullRequestStatus context: 'test', state: 'ERROR'
        setGitHubPullRequestStatus context: 'deploy', state: 'ERROR'
        throw e
    }

    stage "test"
    try {
        sh('sleep 5')
        setGitHubPullRequestStatus context: 'test', state: 'SUCCESS', message: 'All tests passed!'
    } catch (error) {
        setGitHubPullRequestStatus context: 'test', state: 'FAILURE'
        setGitHubPullRequestStatus context: 'deploy', state: 'ERROR'
        throw e
    }

    stage "deploy"
    try {
        sh('sleep 5')
        setGitHubPullRequestStatus context: 'deploy', state: 'SUCCESS', message: 'Successfully deployed build'
    } catch (error) {
        setGitHubPullRequestStatus context: 'deploy', state: 'FAILURE'
        throw e
    }
}





