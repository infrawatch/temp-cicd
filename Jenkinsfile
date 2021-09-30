#!/usr/bin/env groovy

node {
    stage("One"){
        sh script: "git fetch upstream --no-tags aveselov-test", label: "Getting branch"
        def git_diff = sh (
            script: "git diff --name-only HEAD~1",
            returnStdout: true
        ).trim()
        println git_diff
    }
}
