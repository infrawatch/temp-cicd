
#!/usr/bin/env groovy

node('master') {
    checkout scm
    stage('set Jenkins properties') {
        properties([
            pipelineTriggers([
                issueCommentTrigger('.*run test')
            ])
        ])
    }
    stage('triggers') {
        def triggerCause = currentBuild.rawBuild.getCause(org.jenkinsci.plugins.pipeline.github.trigger.IssueCommentCause) 
        if (triggerCause) {
            echo("Build started by ${triggerCause.userLogin}, sob wrote \"${triggerCause.comment}\"")
        } else {
            echo("build not start by a trigger")
        }
    }
}
