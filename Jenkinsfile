def resp = httpRequest 'https://raw.githubusercontent.com/infrawatch/service-telemetry-operator/master/Makefile'

println("status: " + resp.status)
println("content: " + resp.content)

properties([
    pipelineTriggers([
        issueCommentTrigger(".*")
    ])
])

@NonCPS
def isComment() {
    def triggerCause = currentBuild.rawBuild.getCause(com.adobe.jenkins.github_pr_comment_build.GitHubPullRequestCommentCause) 
    if (triggerCause) {
        echo("Comment URL ${triggerCause.commentUrl}, sob wrote \"${triggerCause.commentBody}\"")
    }
}

@NonCPS
def isReview() {
    def triggerCause = currentBuild.rawBuild.getCause(com.adobe.jenkins.github_pr_comment_build.GitHubPullRequestReviewCause) 
    if (triggerCause) {
        echo("Review URL ${triggerCause.pullRequestUrl}")
    }
}

isComment()
isReview()

node('master'){
    stage('Check Validity'){
        checkout scm 
        
    }
    stage('Check'){
        script {
            def newJFile = readFile(file: 'Jenkinsfile')
            if (newJFile == resp.content) {
                println "files match"
            } else {
                println "files don't match"
            }
        }
    }
}
