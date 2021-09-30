#!/usr/bin/env groovy

node {
    stage("One"){
        def git_diff = sh (
            script: "git diff --name-only HEAD~1",
            returnStdout: true
        ).trim()
        println git_diff
    }
}