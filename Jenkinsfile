properties([
    pipelineTriggers([
        issueCommentTrigger('.*test*'),
    ])
])

def triggerCause = currentBuild.rawBuild.getCause(org.jenkinsci.plugins.pipeline.github.trigger.IssueCommentCause) 
if (triggerCause) {
    echo("Build started by ${triggerCause.userLogin}, sob wrote \"${triggerCause.comment}\"")
    println triggerCause
    
    // get Jenkinsfile in branch master
    def resp = httpRequest 'https://raw.githubusercontent.com/infrawatch/service-telemetry-operator/master/Makefile'
    println("status: " + resp.status)
    println("content: " + resp.content)

} else {
    echo('Build was not started by a trigger')
}
