properties([
    pipelineTriggers([
        issueCommentTrigger('.*test*'),
    ])
])

def resp = httpRequest 'https://raw.githubusercontent.com/infrawatch/service-telemetry-operator/master/Makefile'
println("status: " + resp.status)
println("content: " + resp.content)

def triggerCause = currentBuild.rawBuild.getCause(com.adobe.jenkins.github_pr_comment_buildi.GitHubPullRequestCommentCause) 
if (triggerCause) {
    echo("Comment URL ${triggerCause.commentUrl}, sob wrote \"${triggerCause.commentBody}\"")
} else {
    echo('Build was not started by a trigger')
}

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
