def gitStatusUpdate(state, description) {
    sh """
        curl \\
            -X POST \\
            -H "Content-Type: application/json" \\
            -H "Authorization: token ebf828c4a3152c8264537e254756fb9d2e349984" \\
            -d '{
                "state": "${state}",
                "target_url": "${BUILD_URL}console",
                "description": "${description}",
                "context": "continuous-integration/jenkins"
            }' \\
        "https://api.github.com/repos/${GIT_USERNAME}/${GIT_REPO_NAME}/statuses/${GIT_AFTER_HASH}"
    """
}


node {
    stage("Initialisation") {        
        gitStatusUpdate("pending", "Initialising Jenkins Workspace")

        dir('repo') {
            checkout scm
        }
    }

    stage("Done") {
        echo "\n\n\n"
        sh "cd repo"
        sh "ls -la"
        sh "cd repo"
        sh "ls -la"
        sh "rm -R repo"
        gitStatusUpdate("success", "Done n stuff")
    }
}