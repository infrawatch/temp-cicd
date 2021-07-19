properties([
    pipelineTriggers([
        issueCommentTrigger('.*test*'),
    ])
])

def triggerCause = currentBuild.rawBuild.getCause(org.jenkinsci.plugins.pipeline.github.trigger.IssueCommentCause) 
if (triggerCause) {
    echo("Build started by ${triggerCause.userLogin}, sob wrote \"${triggerCause.comment}\"")
    println triggerCause
} else {
    echo("build not start by a trigger")
}


pullRequest.comment('this sucks')
