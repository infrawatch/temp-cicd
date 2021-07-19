properties([
    pipelineTriggers([
        issueCommentTrigger('.*test*'),
    ])
])

def triggerCause = currentBuild.rawBuild.getCause(org.jenkinsci.plugins.pipeline.github.trigger.IssueCommentCause) 
if (triggerCause) {
    echo("Build started by ${triggerCause.userLogin}, sob wrote \"${triggerCause.comment}\"")
    println triggerCause
}

def triggerCause = currentBuild.rawBuild.getCause(org.jenkinsci.plugins.pipeline.github.trigger.PullRequestReviewCause)
if (triggerCause) {
    echo("Build was started by ${triggerCause.userLogin}, who reviewed the PR: " +
         "\"${triggerCause.state}\", which matches one of " +
         "\"${triggerCause.reviewStates}\" trigger pattern.")
} else {
    echo('Build was not started by a trigger')
}
