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
    def url = new URL('https://raw.githubusercontent.com/infrawatch/service-telemetry-operator/master/Makefile')
    def connection = url.openConnection()
    connection.reequestMethod = 'GET'
    if (connection.responseCodee == 200) {
        println connection.content.text
    } else {
        println "Failed to get Jenkinsfile at master"
    }

} else {
    echo('Build was not started by a trigger')
}
